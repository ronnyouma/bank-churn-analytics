# 💳 Bank Customer Churn Analytics

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-SQLite-003B57?style=flat&logo=sqlite&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-Public-E97627?style=flat&logo=tableau&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google-Sheets-34A853?style=flat&logo=googlesheets&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-success?style=flat)

An end-to-end finance analytics project analysing **10,000 bank customers** across France, Germany and Spain to uncover the key drivers of customer churn and quantify the revenue impact of customer attrition.

🔗 [View Interactive Tableau Dashboard](https://public.tableau.com/views/BankCustomerChurnAnalytics_17792719438120/ChurnAnalyticsDashboard?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) &nbsp;|&nbsp; 📋 [View Google Sheets Documentation](https://docs.google.com/spreadsheets/d/1t18QI3kwer97S9Rshe_CrvZeQ2n9tOCOJYHFQ9XGZ5U/edit?usp=sharing)

---

## 📌 Business Problem

Customer churn is one of the most costly challenges facing retail banks. Acquiring a new customer costs 5–7× more than retaining an existing one. This project identifies which customer segments are at highest risk of leaving, what behavioural signals precede churn, and where targeted retention efforts would generate the greatest return.

---

## 🔑 Key Findings

| Finding | Detail |
|---|---|
| Overall churn rate | 20.37% across 10,000 customers |
| Highest churn geography | Germany at ~32% — nearly 2× France and Spain |
| Highest churn age band | 40–49 year olds at ~35% churn rate |
| Product paradox | Customers with 3–4 products churn at dramatically higher rates |
| Inactivity signal | Inactive members churn at 2× the rate of active members |
| Gender gap | Female customers churn at ~25% vs ~16% for male customers |
| Revenue impact | ~15% of estimated salary lost per churned customer |

---

## 🗂 Project Structure

```
bank-churn-analytics/
│
├── notebooks/
│   ├── 01_setup_and_load.ipynb                  # Phase 1 — Data acquisition & SQLite setup
│   ├── 02_sql_data_cleaning.ipynb               # Phase 2 — SQL cleaning & feature engineering
│   └── 03_eda_and_feature_engineering.ipynb     # Phase 3 — EDA, visualisations & export
│
├── sql/
│   └── 01_load_and_inspect.sql                  # Raw SQL inspection queries
│
├── .gitignore
└── README.md
```

> **Note:** The raw dataset (`Churn_Modelling.csv`) and SQLite database (`churn.db`) are excluded from this repository due to file size. See the **Getting Started** section below to download them.

---

## 🛠 Tech Stack

| Tool | Purpose |
|---|---|
| Python (Pandas, NumPy) | Data loading, cleaning, feature engineering |
| Matplotlib & Seaborn | EDA visualisations including KDE plots and heatmap |
| SQL (SQLite) | Data transformation, type casting, QA validation |
| Jupyter Notebook | Analysis environment and documentation |
| Google Sheets | Data dictionary, KPI summary, pivot tables, insights brief |
| Tableau Public | Interactive dashboard with advanced interactivity |

---

## 📊 Dashboard Preview

> 🔗 [View the full interactive dashboard on Tableau Public](https://public.tableau.com/views/BankCustomerChurnAnalytics_17792719438120/ChurnAnalyticsDashboard?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

Built with a **Warm Graphite** dark theme (`#2D2D2D` / `#3D3D3D`), the dashboard includes:

- 5 KPI tiles — total customers, churn rate, churned count, avg age of churned, revenue at risk
- Churn rate by geography (symbol map with dark tile)
- Churn rate by age band (bar chart with reference line)
- Customer value tier breakdown (donut chart)
- Churn rate by number of products held (bar chart)
- Churn rate by customer tenure (line chart with trend line)
- Dynamic segmentation chart (parameter-controlled — switches between Gender, Active Member, Geography)
- Dashboard actions — clicking any chart filters all others simultaneously
- Dynamic filters — Geography, Gender, Age Band, Value Tier, Active Member

---

## ⚙️ Getting Started

### 1 — Clone the repository
```bash
git clone https://github.com/yourusername/bank-churn-analytics.git
cd bank-churn-analytics
```

### 2 — Install dependencies
```bash
pip install pandas numpy matplotlib seaborn sqlalchemy jupyter
```

### 3 — Download the dataset
Download the dataset from Kaggle:
👉 [kaggle.com/datasets/shubh0799/churn-modelling](https://www.kaggle.com/datasets/shubh0799/churn-modelling)

Place `Churn_Modelling.csv` inside a `data/` folder in the project root:
```
bank-churn-analytics/
└── data/
    └── Churn_Modelling.csv
```

### 4 — Run the notebooks in order
```bash
jupyter notebook
```
Open and run each notebook in sequence:
1. `01_setup_and_load.ipynb`
2. `02_sql_data_cleaning.ipynb`
3. `03_eda_and_feature_engineering.ipynb`

---

## 🔬 Methodology

### Phase 1 — Data Acquisition & Setup
- Downloaded the Bank Customer Churn Modelling dataset from Kaggle
- Loaded 10,000 rows × 14 columns into a local SQLite database
- Confirmed zero nulls and zero duplicates in the raw data

### Phase 2 — SQL Data Cleaning & Feature Engineering
- Dropped 2 irrelevant columns: `RowNumber` and `Surname`
- Engineered 4 new features:
  - `age_band` — groups customers into 5 decade brackets
  - `balance_segment` — segments account balance into 5 tiers
  - `credit_band` — categorises credit score from Poor to Exceptional
  - `value_tier` — composite score combining balance, products, activity and tenure
- Ran a 7-point automated QA check — all passed

### Phase 3 — EDA & Feature Engineering
- Produced 9 charts covering churn by geography, age, products, gender, activity and tenure
- Built a correlation heatmap identifying age and active membership as top predictors
- Engineered 2 additional features:
  - `revenue_at_risk` — estimated revenue lost per churned customer (15% of salary)
  - `engagement_score` — composite metric combining tenure, activity, products and credit card
- Exported clean dataset for Tableau

### Phase 4 — Google Sheets Documentation
- Built a full data dictionary covering all 18 columns
- Created a KPI summary for non-technical stakeholders
- Built 5 pivot tables independently validating Python findings
- Wrote a retention-focused insights brief with 5 findings and actionable recommendations

### Phase 5 — Tableau Dashboard
- Connected cleaned CSV export to Tableau Public
- Created 4 calculated fields including an LOD-style average age expression
- Built a parameter control allowing dynamic chart segmentation
- Configured dashboard actions for cross-chart drill-down filtering
- Applied Warm Graphite dark theme consistently across all sheets and tiles
- Published to Tableau Public

---

## 💡 Retention Recommendations

| Priority | Action | Target Segment |
|---|---|---|
| 🔴 High | Deploy country-specific retention campaign | German customers |
| 🔴 High | Trigger re-engagement for inactive members | 90+ days inactive |
| 🟠 Medium | Launch loyalty programme | Customers aged 40–60, 3+ years tenure |
| 🟠 Medium | Audit product bundling strategy | Customers with 3–4 products |
| 🟡 Low | Review female customer experience | All female customers |

Targeting the top two priorities alone could reduce overall churn by an estimated **4–6 percentage points** — retaining **400–600 additional customers** annually.

---

## 🆕 New Tableau Skills vs Previous Project

| Skill | Hospital Project | Churn Project |
|---|---|---|
| Chart types | Bar, donut | Bar, donut, symbol map, line |
| Calculated fields | None | 4 custom fields |
| LOD expressions | None | Avg Age Churned |
| Parameter controls | None | Dynamic segment switcher |
| Dashboard actions | None | Click-to-filter drill-downs |
| Theme | Dark navy | Warm graphite |

---

## 📁 Data Source

**Bank Customer Churn Modelling**
- Source: [Kaggle](https://www.kaggle.com/datasets/shubh0799/churn-modelling)
- Records: 10,000 customers · 14 features
- Geography: France, Germany, Spain
- Note: Simulated banking dataset for analytical purposes

---

## 👤 Author

**Ronny Ouma**
Junior Data Analyst | Finance & Analytics

🔗 [LinkedIn](https://www.linkedin.com/in/ronny-ouma-49b070367?utm_source=share_via&utm_content=profile&utm_medium=member_android) &nbsp;|&nbsp; 📊 [Tableau Public](https://public.tableau.com/app/profile/ronny.ouma/vizzes) &nbsp;|&nbsp; 💻 [GitHub](https://github.com/ronnyouma/)

---
