# World Bank Group Scorecard Outcomes Analytics

**Python | SQL | Data Analytics | Interactive Dashboards | Development Results**

## Project Overview

This project analyzes the World Bank Group's FY2025 Scorecard data to explore development results across countries, regions, projects, and outcome indicators.

It demonstrates an end-to-end analytical workflow, from data ingestion and cleaning to SQL-based analysis, interactive visualization, and data-quality assessment.

The project focuses on three questions:

1. How do reported achievements compare with expected results across Scorecard indicators?
2. What does project-indicator progress look like across regions and countries?
3. How do missing data, overlapping observations, and reporting inconsistencies affect the interpretation of results?

## Data

**Source:** World Bank Group FY2025 Scorecard.

The analysis integrates data from three Scorecard components:

* WBG Results
* Client Context
* Vision

The source files contain aggregate indicator data, project-level information, and indicator dictionaries.

## Analytical Methodology

### 1. Data preparation

Excel workbooks were extracted, consolidated, and processed using Python and pandas.

The workflow includes data-type conversion, missing-value assessment, identification of repeated observations, and construction of analytical datasets.

### 2. Aggregate Scorecard analysis

Country-level achieved and expected results were examined by indicator.

Achievement ratios were calculated only where expected results were positive and the necessary values were available.

These ratios describe reported achievement relative to expected results; they do not independently establish whether an indicator is on schedule.

### 3. Project-indicator progress

For indicators with increasing targets, progress was calculated as:

**Progress (%) = (Current − Baseline) / (Target − Baseline) × 100**

Indicators with unchanged or decreasing targets were excluded from this specific calculation.

The cleaned analytical dataset contains **11,197 unique project-indicator observations** with calculable progress.

### 4. SQL analysis

DuckDB was used to query project-level data and produce regional and indicator-level summaries.

Queries calculate observation counts, distinct project counts, median progress, and the proportion of observations exceeding their targets.

### 5. Interactive dashboard

An interactive dashboard built with Plotly and ipywidgets enables users to explore:

* Scorecard indicators
* Regional progress summaries
* Country-level results
* Individual projects and their indicators
* Data-quality filters

### 6. Data-quality assessment

The analysis identifies records requiring additional review, including missing reporting dates, inconsistent date sequences, negative progress, and extreme progress ratios.

Of 11,197 analytical observations, **3,325 have at least one quality flag**, while **7,872 have none under the implemented checks**.

Quality flags are diagnostic indicators, not automatic evidence of erroneous data.

## Key Analytical Findings

The project demonstrates substantial variation in reported progress across indicators and geographic areas. However, these descriptive differences should not be interpreted as comparative performance assessments without accounting for differences in project maturity, indicator definitions, and reporting practices.

The analysis also identifies several methodological considerations:

* Total, Female, and Youth observations may overlap and must not be summed indiscriminately.
* Multiple project indicators can map to a single Scorecard indicator.
* Extreme achievement ratios may reflect genuine target exceedance, small denominators, or reporting inconsistencies.
* Progress relative to a final target does not establish whether a project is on schedule.

## Technology Stack

| Tool             | Application                      |
| ---------------- | -------------------------------- |
| Python           | Data processing and analysis     |
| pandas and NumPy | Data cleaning and transformation |
| DuckDB / SQL     | Analytical queries               |
| Plotly           | Interactive visualizations       |
| ipywidgets       | Dashboard controls               |
| Google Colab     | Development environment          |

## Repository Contents

* `WBG_Scorecard_Outcomes_Analytics.ipynb` — Main analytical notebook and dashboard.
* `WBG_Scorecard_Analytics_Outputs.zip` — Exported analytical datasets and summary tables.

## Limitations

This project uses the FY2025 Scorecard data snapshot and provides descriptive analytics rather than causal impact evaluation.

Project-indicator progress is calculated only for records with increasing targets and available values. Aggregate WBG Results observations represent a single reporting snapshot and are not sufficient for time-series forecasting.

Regional and country medians summarize heterogeneous project indicators and should not be interpreted as performance rankings.

## Reproducibility

The notebook documents the analytical workflow and includes the Python and SQL code used to generate the outputs.

Reproducing the complete pipeline requires the corresponding source workbooks from the World Bank Group Scorecard data portal.

## Disclaimer

This is an independent portfolio project developed using publicly available World Bank Group data. It is not an official World Bank Group publication or assessment.
