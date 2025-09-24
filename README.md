# 🚦 Chicago Traffic Crash Severity Analysis

## 🎯 Project Objective
This project aims to **identify and predict the key factors** contributing to **severe injuries** (Fatal or Incapacitating) in traffic crashes reported by the Chicago Police Department (CPD) from 2016 to 2024. The analysis addresses a significant **class imbalance** challenge, as approximately 18.6% of crashes result in severe injuries.

## 📊 Data Source
* **Source:** Chicago Police Department (CPD) Traffic Crash Reports.
* **File:** `ChicagoTrafficCrash.csv`
* **Timeframe:** 2016 to 2024.

## 📁 Repository Contents

| File Name | Description |
| :--- | :--- |
| `Data_Project.Rmd` | **The complete source code and narrative** for the analysis, including data wrangling, model fitting, and interpretation. This is the **reproducible script** for the entire project. |
| `Project.docx` | The **final, knitted output report** containing all text, tables, plots, and model summaries, viewable without R. |
| `Project.R` | (Placeholder/Supplementary R script, if used for functions or final models). |
| `ChicagoTrafficCrash.csv`| The primary dataset used for the analysis. |

---

## 🔑 Key Analytical Findings
The modeling and exploratory analysis confirmed several highly significant factors influencing severe injury outcomes:

### Predictive Performance (AUC on Test Set)
The **Gradient Boosting Machine (GBM)** provided the best predictive balance, achieving the highest Area Under the Curve (AUC) on the test set.

| Model | Test AUC |
| :--- | :--- |
| **Gradient Boosting Machine (GBM)** | **0.606** |
| Lasso Regression | 0.603 |
| Random Forest (RF) | 0.569 |
| Bagging | 0.566 |
| CART | 0.554 |

### Top Risk Factors & Interpretation
Both model-based and dimensionality reduction techniques highlighted the following as dominant factors:

1.  **Driver Behavior & Impairment:** Crashes involving **pedestrians**, **physical driver impairment** (Lasso Odds Ratio: $\approx$ 1.85), and driving **under the influence of alcohol/drugs** significantly increase severe injury odds.
2.  **Speed Limits:** The probability of a severe injury notably **increases with rising posted speed limits, particularly above 35 mph**.
3.  **Crash Type & Location:** **First Crash Type**, **Primary Contributory Cause**, and **Trafficway Type** were found to be the most strongly associated variables (Cramér's V $\approx$ 0.10). **Intersection involvement** and **adverse weather** (snow/rain) were also critical categorical drivers identified by Multiple Correspondence Analysis (MCA).

---

## 💡 Actionable Recommendations (Policy Translation)
Based on the data, the following interventions are recommended to mitigate severe injuries in Chicago traffic:

* **Speed Enforcement:** Enhance speed enforcement and regulations, focusing on high-speed road segments (>35 mph).
* **Infrastructure:** Implement targeted upgrades, including improved street lighting and safer pedestrian crossings.
* **Interventions:** Strengthen educational and regulatory programs aimed at reducing impaired driving behaviors.
* **Adverse Conditions:** Implement intersection-specific improvements and preventative measures, particularly during adverse weather.

---

## 🛠️ Reproduction & Dependencies

To reproduce this analysis locally, you will need **R** (version $\geq$ 3.4.0) and the following packages:

```R
# Core Packages for Data Wrangling and Reporting
install.packages(c("dplyr", "naniar", "forcats", "rsample"))

# Modeling and Interpretation Packages
install.packages(c("caret", "pROC", "MASS", "glmnet", "fastshap", "pdp"))

# Dimensionality Reduction and Visualization
install.packages(c("FactoMineR", "factoextra"))

# Knit the Rmd file (requires the 'rmarkdown' package, often pre-installed)
rmarkdown::render("Data_Project.Rmd")
