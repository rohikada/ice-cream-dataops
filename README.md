# 🍦 Ice Cream Factory DataOps – Cognite Bootcamp Project

Welcome to the **Ice Cream Factory DataOps** repository!  
This project was developed as part of the **Cognite Data Fusion (CDF) Technical Bootcamp**, showcasing a complete end-to-end implementation of a **production-ready industrial data solution** using Cognite's platform, Python SDK, CI/CD pipelines, and industrial tools.

---

## 🎯 Use Case: Overall Equipment Effectiveness (OEE)

The goal of this project is to calculate and monitor **Overall Equipment Effectiveness (OEE)** for various assets in an industrial setting (Ice Cream Factory).  
OEE is a key metric in manufacturing that combines **Availability**, **Performance**, and **Quality** to assess how effectively equipment is being used.

---

## 📊 Data Used

- **Source**: [Ice Cream Factory REST API](https://ice-cream-factory.inso-internal.cognite.ai/docs#/)
- **Types**:
  - **Assets**: Factory equipment and hierarchy
  - **Time Series**: Sensor data like `count`, `good`, `status`, `planned_status`
  - **Files**: Engineering diagrams (P&ID)
- **Use Case**: OEE calculation based on native time series
---

## 🧰 Implementation Overview

### 1. 🔐 **Data Foundation**
- Created Entra ID groups and mapped them to CDF groups
- Defined datasets, RAW tables, and data modeling spaces
- Used `.env` and `config.test.yaml` for environment setup

### 2. 🔄 **Data Integration**
- **Hosted Extractors**: Ingested assets and time series from REST API
- **Custom Extractors**: Deployed as Cognite Functions for datapoints
- **Extraction Pipelines**: Monitored extractor health

### 3. 🧬 **Data Modeling**
- Used **Transformations** to contextualize assets and time series
- SQL-based logic deployed via CDF Toolkit
- Scheduled transformations using `.schedule.yaml`

### 4. 🔁 **Data Orchestration**
- Defined **Workflows** to coordinate extractors, transformations, and functions
- Scheduled execution every 15 minutes using cron triggers

### 5. ⚙️ **DevOps & CI/CD**
- Used **GitHub Actions** to deploy configurations to test and prod
- Managed secrets and environment variables securely
- Verified deployments via Fusion UI

### 6. 📈 **Industrial Tools**
- **Charts**: Visualized OEE and its components
- **Canvas**: Performed root cause analysis of OEE drops
---

## 📁 Repository Structure

```bash
ice-cream-dataops/
├── modules/
│   └── bootcamp/
│       ├── data_foundation/
│       ├── ice_cream_api/
│       │   ├── hosted_extractors/
│       │   ├── transformations/
│       │   ├── extraction_pipelines/
│       │   ├── raw/
│       │   ├── data_sets/
│       │   ├── data_models/
│       └── use_cases/
│           └── oee/
│               ├── functions/
│               ├── data_sets/
│               ├── data_models/
│               ├── auth/
├── config.test.yaml
├── config.prod.yaml
├── .github/
    └── workflows/
        └── deploy.yaml
```
---

## 🚀 How to Run Locally
To get started with the project locally, follow these steps:

### 1. 🔧 Clone the repository:
```
git clone https://github.com/rohikada/ice-cream-dataops.git
cd ice-cream-dataops
```

### 2. 🛠️ Set up Python environment:
```
pyenv install 3.11
pyenv global 3.11
poetry install
```

✅ Note: Make sure you have pyenv and poetry installed before running the above commands.

### 3. 🔐 Configure environment variables:
- Create a ```.env``` file at the root of the project and add your credentials and configuration values.

### 4. 🚀 Deploy Modules:
```
cdf build
cdf deploy --dry-run
cdf deploy
```

### 5. 📊 Monitor in Fusion UI
- Navigate to Data Management → Integrate → Data Workflows to verify workflow execution.
- Use Industrial Tools → Search to explore ingested assets, time series, and files.
---

## 📄 License
This project is intended for educational and demonstration purposes under the Cognite Bootcamp.
Please refer to Cognite’s licensing terms for more information.
