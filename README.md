# E-Commerce Sales & Customer Analytics — RFM Segmentation

An end-to-end data analytics project on the UCI Online Retail dataset — from raw transaction data to a 3-page Power BI dashboard, covering data cleaning, RFM (Recency, Frequency, Monetary) customer segmentation, sales trend analysis, and cohort retention analysis.

## Business Problem

An online retailer wants to understand **which customers are most valuable, which are at risk of churning, and how sales are trending** — so the business can prioritize retention campaigns and marketing spend where it matters most.

## Dataset

**Source:** [Online Retail dataset (UCI Machine Learning Repository)](https://www.kaggle.com/datasets/luisrenterialezano/retail-sales-dataset) — real transactional data from a UK-based online retailer, Dec 2010 – Dec 2011.

> Note: The raw dataset (`online_retail.csv`, ~45MB) and the cleaned intermediate file (`transactions.csv`) are not included in this repo due to GitHub's file size limits. Download the raw dataset from the UCI link above and place it alongside the notebook to reproduce the full pipeline — running the notebook regenerates `transactions.csv` automatically.

- `rfm_segments.csv` — customer-level RFM scores and segment labels (4,338 customers)
- `monthly_sales.csv` — aggregated monthly revenue trend

## Project Structure
├── Ecommerce_project.ipynb # Full analysis notebook
├── rfm_segments.csv # Customer RFM scores & segments
├── monthly_sales.csv # Monthly revenue trend
├── E-Commerce_Sales___Customer_Analytics_Dashboard.pbix # 3-page Power BI dashboard
└── README.md


## Workflow

1. **Data Cleaning (Python/Pandas)** — Removed rows with missing CustomerID, filtered out negative quantities/prices (returns), removed cancelled orders (InvoiceNo starting with 'C'), calculated `TotalAmount` (Quantity × UnitPrice).
2. **RFM Analysis** — Calculated Recency (days since last purchase), Frequency (number of unique orders), and Monetary (total spend) per customer, then scored each on a 1–5 scale using quantile binning.
3. **Customer Segmentation** — Combined RFM scores into segments: Champions, Loyal Customers, Promising, At Risk, Can't Lose, and Lost.
4. **Sales Trend Analysis** — Aggregated monthly revenue to identify seasonal patterns.
5. **Top Products Analysis** — Ranked products by total revenue contribution.
6. **Cohort Retention Analysis** — Tracked customer retention by first-purchase month using a cohort heatmap.
7. **Power BI Dashboard** — Built a 3-page interactive dashboard ("E-Commerce Sales & Customer Analytics Dashboard"):
   - **Page 1 — Sales Overview:** KPI cards (Total Sales, Total Orders, Total Customers, AOV), monthly sales trend line chart, top products bar chart
   - **Page 2 — Customer Segmentation:** Segment KPIs, segment distribution donut chart, monetary value by segment, interactive slicers (Segment, Country)
   - **Page 3 — Geographic & RFM Detail:** Country-wise sales bar chart, sales map, RFM score pivot table

## Key Findings

- **Champions (962 customers)** and **Loyal Customers (758)** are the highest-value segments and drive a disproportionate share of revenue.
- **Lost customers (824)** represent a significant churned base — a major retention opportunity.
- **At Risk (643) + Can't Lose (241)** customers were previously valuable but have gone quiet — prime targets for win-back campaigns.
- Sales show **clear seasonal peaks** (Sep–Nov, likely pre-holiday buying).
- Total Revenue: **£8.91M** across **18,532 orders** from **4,338 customers**.

## Business Recommendations

1. Offer Champions & Loyal Customers exclusive early access and loyalty rewards.
2. Run personalized win-back campaigns (discounts + reminders) for At Risk / Can't Lose segments.
3. Give Promising (new) customers onboarding incentives to convert them into Loyal.
4. Run low-budget re-activation campaigns for Lost customers.
5. Prioritize retention over acquisition — retaining existing customers is more cost-effective than acquiring new ones.

## Tools & Skills Demonstrated

Python · Pandas · NumPy · Matplotlib · Seaborn · Data Cleaning · RFM Analysis · Customer Segmentation · Cohort Analysis · Power BI · DAX · Data Visualization · Business Analytics

## How to Run

1. Download `online_retail.csv` from the [UCI dataset link](https://www.kaggle.com/datasets/luisrenterialezano/retail-sales-dataset) and place it alongside the notebook.
2. Open `Ecommerce_project.ipynb` in Jupyter Notebook or Google Colab and run all cells — this regenerates `transactions.csv`, `rfm_segments.csv`, and `monthly_sales.csv`.
3. Open `E-Commerce_Sales___Customer_Analytics_Dashboard.pbix` in Power BI Desktop to explore the interactive dashboard.
