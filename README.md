# Store Trial Analysis

## Overview
This project is part of the Quantium Virtual Internship and focuses on evaluating the performance of a store trial conducted in stores 77, 86, and 88. The analysis compares the trial stores against carefully selected control stores using key monthly metrics to determine if the trial interventions led to a significant uplift in sales and customer activity.

## Project Objectives
- **Control Store Selection:**  
  Identify control stores that closely match each trial store's historical performance prior to the trial period (Feb 2019) based on:
  - Total sales revenue
  - Number of customers
  - Transactions per customer
- **Performance Comparison:**  
  Evaluate the trial store performance during the trial period (March–June 2019) against the matched control stores.
- **Statistical Assessment:**  
  Quantify the impact of the trial by calculating percentage differences, scaling control performance, and performing statistical tests (e.g., t-tests).
- **Visualization & Insights:**  
  Generate visualizations (time series plots, confidence intervals) to clearly communicate the performance differences and support strategic recommendations.

## Data Description
- **Input Data:**  
  The analysis uses the merged dataset (`QVI_data.csv`) generated in Task 1, which includes:
  - Transaction details (e.g., `TOT_SALES`, `PROD_QTY`, `TXN_ID`)
  - Customer demographics (e.g., `LIFESTAGE`, `PREMIUM_CUSTOMER`)
  - A calculated `YEARMONTH` field derived from the transaction `DATE`
- **Key Metrics:**  
  For each store by month, the following metrics are calculated:
  - **totSales:** Total sales revenue
  - **nCustomers:** Number of unique customers
  - **nTxnPerCust:** Transactions per customer
  - **nChipsPerTxn:** Average chips per transaction
  - **avgPricePerUnit:** Average price per unit of chips

## Methodology & Approach
1. **Metric Calculation:**  
   - Aggregate the merged dataset by store and month to compute key performance indicators.
   - Create a `YEARMONTH` column (format: yyyymm) for time series analysis.

2. **Pre-Trial Filtering:**  
   - Identify stores with full observation during the pre-trial period (Feb 2018 to Jan 2019).
   - Filter metrics to include only these stores for accurate control matching.

3. **Control Store Selection:**  
   - Define functions to compute the **Pearson correlation** and **standardized magnitude distance** for key metrics (e.g., totSales and nCustomers) between a trial store and potential control stores.
   - Combine the scores (with equal weights) to derive a composite score.
   - Select the control store for each trial store as the candidate (other than the trial store itself) with the highest composite score.

4. **Trial Assessment:**  
   - Scale the control store’s pre-trial performance to align with the trial store’s performance.
   - Compare the scaled performance with the trial store’s performance during the trial period.
   - Calculate the percentage difference and perform t-tests using pre-trial variability as a benchmark.
   - Visualize trends and confidence intervals to assess if the trial led to significant uplift.

