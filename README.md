# 📉 Telco Customer Churn Analysis
### AI-Assisted End-to-End Data Science Project

> Built as part of the **AI for Data Analysis** course — Orange Digital Center  
> Demonstrates how AI tools can accelerate and deepen a complete data science workflow without sacrificing analytical rigor.

---

## 🗂 Project Overview

This project tackles one of the most common and costly problems in the telecom industry — customer churn. Using the IBM Watson Telco Customer Churn dataset (7,043 customers · 21 features), the analysis moves through five complete stages: data understanding, preprocessing, exploratory analysis, machine learning modeling, and business cost simulation.

The result is not just a model — it's a full analytical product: documented notebooks, a professional presentation deck, a retention strategy memo, and a break-even simulation that translates model outputs into dollar figures.

---

## 🤖 AI-Assisted Workflow

This project was built using AI as a **thinking partner and productivity multiplier** at every stage — not just for code generation, but for analytical reasoning, business interpretation, and communication design.

| Stage | How AI Was Used |
|-------|----------------|
| **Data Understanding** | Mapped column dependencies, identified gated relationships, and flagged non-obvious quality issues before writing a single line of code |
| **Preprocessing** | Reasoned through ambiguous decisions — e.g. why `TotalCharges = 0` for `tenure = 0` customers is semantically correct, not missing data |
| **EDA** | Translated statistical patterns into business language and identified the Fiber × No Tech Support intersection (50% churn) as a critical insight |
| **Modeling** | Justified metric prioritization (Recall over Accuracy for churn), explained threshold tuning, and interpreted cross-validation stability |
| **Cost Simulation** | Structured the full financial model — CLV calculation, CAC waste, break-even logic, and the retention strategy memo |
| **Presentation** | Generated a 11-slide professional deck with real EDA charts embedded, themed to match the dataset's narrative |

**The outcome:** a project that would typically take weeks was completed at professional depth in a fraction of the time — with every decision documented and justified.

---

## 📁 Repository Structure
```
telco-churn-analysis/
│
├── 📓 01_preprocessing.ipynb       # Data cleaning, encoding, type fixes, train-test split
├── 📓 02_EDA.ipynb                 # Demographics, services, tenure, charges analysis
├── 📓 03_modeling.ipynb            # Logistic Regression, Random Forest, XGBoost + evaluation
├── 📓 04_cost_simulation.ipynb     # Revenue loss, retention strategies, break-even analysis
│
├── 📊 telco_churn_presentation.pptx  # 11-slide professional presentation deck
│
├── 📂 data/
│   └── WA_Fn-UseC_-Telco-Customer-Churn.csv
│
└── 📄 README.md
```

---

## 🔬 Project Stages

### Stage 1 — Data Understanding & Preprocessing
- Full column-by-column analysis with dependency mapping
- 9 data quality issues identified and documented
- Key fixes: `TotalCharges` string → float, `SeniorCitizen` int → Yes/No, collapsing redundant third-state values in 7 gated columns
- Stratified 80/20 train-test split preserving the 73.5/26.5 churn ratio
- **0 rows dropped** — all 7,043 records retained

### Stage 2 — Exploratory Data Analysis
- Churn rate analysis across demographics, services, contract type, tenure, and monthly charges
- Key finding: Fiber optic + No Tech Support = **50% churn rate**
- Key finding: Month-to-month customers churn at **43%** vs **3%** on two-year contracts
- Key finding: **47% of all churn happens in the first 12 months**
- Feature interaction heatmaps, KDE distributions, boxplots, and segmentation charts

### Stage 3 — Machine Learning Modeling

Three models trained with class balancing on the stratified split:

| Model | Accuracy | Recall | F1 | ROC-AUC |
|-------|----------|--------|----|---------|
| Logistic Regression | 74.8% | 77.2% | 58.3% | 0.842 |
| Random Forest | 79.4% | 75.6% | 63.2% | 0.840 |
| **XGBoost ✦** | **80.6%** | **79.1%** | **65.8%** | **0.851** |

- ROC curve comparison and confusion matrix visualizations for all three models
- 5-fold stratified cross-validation stability check
- Threshold analysis to find the optimal classification cutoff beyond the default 0.5
- Feature importance ranked by consensus across all three models

### Stage 4 — Cost Simulation & Retention Strategy

**Revenue impact of churn:**
- Monthly revenue lost: **~$139K / month**
- Annual revenue lost: **~$1.67M / year**
- CAC wasted on churners: **~$370K**

**Two retention strategies simulated:**

| | Strategy A — Discount | Strategy B — Loyalty Perks |
|-|----------------------|---------------------------|
| Mechanic | 20% bill discount · 6 months | Free Tech Support + Security · 12 months |
| Retention Rate | ~45% | ~35% |
| Net Recovered | ~$1.8M | ~$1.2M |
| Break-even | < 5% retention needed | ≥ 12% retention needed |
| Risk | Trains price-hunting behavior | Addresses root cause |

**Prime target segment:** High Risk × High Value (~650 customers · $1.1M annual revenue at risk)

---

## 🏆 Top 5 Churn Drivers

Ranked by consensus across Logistic Regression, Random Forest, and XGBoost:

1. **Tenure** — Customers in their first 12 months churn at 47%. Survival past year 1 predicts long-term loyalty.
2. **Contract Type** — Month-to-month has no switching cost. Two-year contracts are near-complete churn insulators.
3. **Total Charges** — Proxy for accumulated relationship value. High totals = long tenure = lower risk.
4. **Monthly Charges** — Higher bills without perceived value accelerate exit. Expensive plans need justification.
5. **Internet Service (Fiber)** — Fiber users churn at 2× DSL rate. Service quality or expectation gap at signup.

---

## 💡 Key Business Recommendations

**01 — Convert month-to-month customers to annual contracts**
A 10% conversion rate on the M2M base prevents ~200+ annual churns. Offer a first-year discount as the incentive.

**02 — Redesign fiber optic onboarding**
A 30-day onboarding call + proactive Tech Support enrollment for new fiber customers addresses the 50% churn intersection at near-zero cost.

**03 — Deploy the XGBoost model monthly**
Score all customers and flag anyone with churn probability > 0.60 for retention outreach. The model catches 79% of actual churners before they leave.

**04 — Focus retention spend on first 12 months**
Nearly half of all churners leave in year 1. Front-loading engagement, perks, and outreach into this window has the highest ROI of any retention investment.

---

## 🛠 Tech Stack

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?style=flat-square&logo=pandas)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.3-F7931E?style=flat-square&logo=scikit-learn)
![XGBoost](https://img.shields.io/badge/XGBoost-2.0-189fdd?style=flat-square)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7-11557c?style=flat-square)
![Seaborn](https://img.shields.io/badge/Seaborn-0.12-4c72b0?style=flat-square)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat-square&logo=jupyter)

---

## 📊 Dataset

**Source:** [IBM Watson Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)  
**Records:** 7,044 customers  
**Features:** 21 columns (demographics, services, account info, financials)  
**Target:** `Churn` — whether the customer left within the last month

---

## 🎓 Course Context

This project was built as the capstone for the **AI for Data Analysis** course at **Orange Digital Center**.  
The course focuses on integrating AI tools into real analytical workflows — using AI not as a shortcut, but as a multiplier that enables analysts to work at greater depth, speed, and communication quality than traditional methods allow.

---

## 📬 Connect

**Abdulrhman Mohamed**  
[Portfolio](https://abdulrhman-mohamed.vercel.app/) · [LinkedIn](https://www.linkedin.com/in/abdulrhman-mohamed-da/) · [YouTube — YeagX](https://youtube.com/@YeagX)
