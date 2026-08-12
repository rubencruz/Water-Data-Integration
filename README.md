# Water Data Integration

A production-oriented data engineering project for ingesting, processing, validating, and transforming water and weather data using **Python, PySpark, and Databricks**.

The project demonstrates modern data engineering practices including **Medallion Architecture, data quality validation, automated testing, CI/CD, environment separation, and cloud-based data processing**.

## Architecture

```text
                    ┌─────────────────────┐
                    │   External APIs     │
                    │  Weather / Water    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Data Ingestion     │
                    │       Python         │
                    └──────────┬──────────┘
                               │
                               ▼
              ┌────────────────────────────────┐
              │          Databricks            │
              │                                │
              │   ┌────────────────────────┐   │
              │   │      Bronze Layer      │   │
              │   │     Raw Data           │   │
              │   └───────────┬────────────┘   │
              │               │                │
              │   ┌───────────▼────────────┐   │
              │   │      Silver Layer      │   │
              │   │ Cleaned & Validated    │   │
              │   └───────────┬────────────┘   │
              │               │                │
              │   ┌───────────▼────────────┐   │
              │   │       Gold Layer       │   │
              │   │ Analytics-Ready Data   │   │
              │   └────────────────────────┘   │
              └────────────────────────────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Analytics / BI /    │
                    │ Downstream Systems  │
                    └─────────────────────┘
```

## Project Goals

The main objective is to build an end-to-end data pipeline that demonstrates how raw data can be transformed into reliable, analytics-ready datasets.

Key engineering objectives include:

* Automated data ingestion
* Distributed data processing with PySpark
* Databricks-based data engineering
* Medallion Architecture
* Data quality and validation
* Structured data transformation
* Automated testing
* CI/CD with GitHub Actions
* DEV and PROD environment separation
* Reproducible deployments
* Cloud-oriented data engineering practices

## Technology Stack

| Technology               | Purpose                                     |
| ------------------------ | ------------------------------------------- |
| Python                   | Data ingestion and application logic        |
| PySpark                  | Distributed data processing                 |
| Databricks               | Cloud data engineering platform             |
| Delta Lake               | Data storage and processing                 |
| Databricks Asset Bundles | Deployment and infrastructure configuration |
| GitHub                   | Source control                              |
| GitHub Actions           | CI/CD automation                            |
| PostgreSQL               | Relational data integration                 |
| Pytest                   | Automated testing                           |
| Docker / Dev Container   | Development environment                     |

## Medallion Architecture

The pipeline follows the **Medallion Architecture** pattern.

### Bronze

The Bronze layer stores the raw ingested data with minimal transformation.

Responsibilities:

* Capture source data
* Preserve the original structure
* Provide traceability
* Support reprocessing

### Silver

The Silver layer contains cleaned and standardized data.

Typical transformations include:

* Data type normalization
* Null handling
* Duplicate removal
* Schema validation
* Data quality rules
* Standardization of attributes

### Gold

The Gold layer contains business-ready datasets optimized for analytics and downstream consumption.

Typical use cases include:

* Aggregations
* Analytical datasets
* Reporting
* BI consumption
* Data products

## Data Quality

Data quality is treated as a first-class component of the pipeline.

Validation can include:

* Schema validation
* Required-field checks
* Null validation
* Duplicate detection
* Data type validation
* Range and consistency checks

This ensures that downstream datasets are reliable and suitable for analytical workloads.

## Environment Strategy

The project separates deployment environments into:

```text
DEV
 │
 ├── Development
 ├── Testing
 └── Validation
        │
        ▼
      PROD
        │
        └── Production workloads
```

This approach allows changes to be developed and validated independently before being promoted to production.

## CI/CD

GitHub Actions is used to automate the development and deployment lifecycle.

The CI/CD workflow is designed to support:

1. Code checkout
2. Python environment setup
3. Dependency installation
4. Automated testing
5. Project validation
6. Databricks Bundle validation
7. Deployment to the target environment

Example workflow:

```text
Developer
    │
    ▼
Git Push / Pull Request
    │
    ▼
GitHub Actions
    │
    ├── Tests
    ├── Validation
    └── Build
          │
          ▼
   Databricks Bundle
          │
          ▼
       DEV / PROD
```

## Testing

Automated tests are implemented using **Pytest**.

Testing focuses on validating:

* Data transformation logic
* Pipeline components
* Data quality rules
* Expected outputs
* Error handling

Tests can be executed locally before changes are committed:

```bash
pytest
```

## Project Structure

```text
Water-Data-Integration/
│
├── 00_Setup_Environment/
│   └── Environment and project configuration
│
├── phase_01/
│   └── 01_Ingestion_Bronze/
│       └── Data ingestion and Bronze layer
│
├── phase_02/
│   └── Data transformation and processing
│
├── .github/
│   └── workflows/
│       └── CI/CD automation
│
├── databricks.yml
├── pyproject.toml
├── README.md
└── ...
```

> The repository is organized into implementation phases to demonstrate the progressive development of the data platform.

## Development Environment

The project can be developed using a local Python environment or a containerized development environment.

Install the project dependencies and configure the required Databricks authentication before executing Databricks workloads.

For local development:

```bash
git clone https://github.com/rubencruz/Water-Data-Integration.git

cd Water-Data-Integration
```

## Databricks Authentication

For local development and CI/CD, Databricks authentication should be configured using secure credentials such as OAuth Service Principal authentication.

Example environment variables:

```bash
DATABRICKS_HOST=<databricks-workspace-url>
DATABRICKS_CLIENT_ID=<client-id>
DATABRICKS_CLIENT_SECRET=<client-secret>
```

**Never commit credentials, tokens, or secrets to the repository.**

## Databricks Asset Bundles

The project uses **Databricks Asset Bundles** to define and deploy Databricks resources consistently across environments.

Typical commands include:

```bash
databricks bundle validate --target dev
```

and:

```bash
databricks bundle deploy --target dev
```

Production deployments can be executed using the corresponding PROD target.

## Engineering Practices Demonstrated

This project was designed to demonstrate practical skills required in modern Data Engineering environments:

* Data ingestion
* ETL / ELT
* PySpark
* Databricks
* Delta Lake
* Medallion Architecture
* Data Quality
* Automated Testing
* CI/CD
* GitHub Actions
* Infrastructure-as-Code principles
* Environment management
* Cloud data platforms
* Production-oriented development practices

## Project Roadmap

### Phase 1 — Ingestion

* [x] Environment setup
* [x] External data ingestion
* [x] Bronze layer implementation

### Phase 2 — Transformation

* [x] Data transformation
* [x] PySpark processing
* [x] Data quality implementation

### Phase 3 — Data Platform

* [ ] Silver layer refinement
* [ ] Gold layer implementation
* [ ] Analytics-ready datasets

### Phase 4 — Deployment

* [x] Databricks Asset Bundles
* [x] DEV environment
* [ ] PROD deployment refinement
* [x] CI/CD pipeline

## Author

**Ruben Cruz**

Data Engineering | Data Integration | PySpark | Databricks | Python | AI Integration

GitHub: https://github.com/rubencruz

---

⭐ If you find this project useful, feel free to explore the repository and its implementation phases.
