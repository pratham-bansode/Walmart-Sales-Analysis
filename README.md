# Walmart Sales Data Analysis

## About

This project focuses on analyzing Walmart sales data using SQL to uncover meaningful business insights. It explores product performance, branch-wise sales, revenue trends, and customer purchasing patterns.

The goal is to understand which products and branches contribute most to business performance, identify sales trends, and discover opportunities to improve sales strategies and customer satisfaction.

The dataset used in this project was obtained from the [Kaggle Walmart Sales Forecasting Competition](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting).

---

## Purpose of the Project

The main purpose of this project is to strengthen SQL and data analysis skills by working with a real-world sales dataset.

This project aims to:

- Analyze Walmart sales and revenue performance.
- Identify top-performing product lines and branches.
- Understand customer purchasing behavior.
- Explore sales trends across different time periods.
- Generate business insights that can support better decision-making.

---

## About the Data

The dataset contains sales transactions from three Walmart branches located in:

- Mandalay
- Yangon
- Naypyitaw

The dataset consists of **1,000 rows and 17 columns**.

### Dataset Information

| Column | Description | Data Type |
|---|---|---|
| invoice_id | Unique invoice number for each transaction | VARCHAR(30) |
| branch | Branch where the sale took place | VARCHAR(5) |
| city | City where the branch is located | VARCHAR(30) |
| customer_type | Type of customer | VARCHAR(30) |
| gender | Gender of the customer | VARCHAR(10) |
| product_line | Category of the purchased product | VARCHAR(100) |
| unit_price | Price of one product unit | DECIMAL(10,2) |
| quantity | Number of products purchased | INT |
| tax_pct | Tax percentage applied to the purchase | FLOAT |
| total | Total amount paid by the customer | DECIMAL(12,4) |
| date | Date of the transaction | DATE |
| time | Time of the transaction | TIME |
| payment | Payment method used by the customer | VARCHAR(15) |
| cogs | Cost of goods sold | DECIMAL(10,2) |
| gross_margin_pct | Gross margin percentage | FLOAT |
| gross_income | Gross income earned from the transaction | DECIMAL(12,4) |
| rating | Customer rating | FLOAT |

---

## Analysis List

### 1. Product Analysis

Analyze the performance of different product lines to identify popular categories, high-revenue products, and areas where product performance can be improved.

### 2. Sales Analysis

Study sales patterns, revenue trends, and branch performance to understand how sales change over time and identify opportunities to improve business strategies.

### 3. Customer Analysis

Explore customer segments, purchasing habits, payment preferences, and ratings to understand customer behavior and improve the overall shopping experience.

---

## Tools and Technologies

- **Database:** MySQL
- **Language:** SQL
- **IDE:** MySQL Workbench
- **Dataset Source:** Kaggle

---

## Approach Used

### 1. Data Wrangling

The first step involves preparing the dataset for analysis.

Tasks performed:

- Created a MySQL database.
- Created the sales table.
- Imported the Walmart sales dataset.
- Defined appropriate data types for each column.
- Used `NOT NULL` constraints for required fields.
- Checked the dataset for missing and NULL values.

### 2. Feature Engineering

New columns were created from existing data to make analysis easier.

#### Time of Day

A new column named `time_of_day` was created to classify transactions into:

- Morning
- Afternoon
- Evening

This helps identify which part of the day has the highest sales activity.

#### Day Name

A new column named `day_name` was created to extract the day of the week from the transaction date.
This helps determine which weekdays are busiest for each branch.

#### Month Name

A new column named `month_name` was created to extract the month from the transaction date.
This helps analyze monthly revenue and profit trends.

### 3. Exploratory Data Analysis (EDA)

SQL queries were used to explore the dataset and answer business questions related to:

- Product performance
- Sales trends
- Customer behavior
- Branch performance
- Revenue and profitability

### 4. Conclusion

The analysis helps identify important sales patterns and customer preferences. These insights can be used to understand business performance and support data-driven decisions.

---

## Business Questions To Answer

### Generic Questions

1. How many unique cities are present in the dataset?
2. Which city does each branch belong to?

---

## Product Analysis

1. How many unique product lines are present in the dataset?
2. What is the most common payment method?
3. Which product line sells the most products?
4. What is the total revenue generated each month?
5. Which month has the highest COGS?
6. Which product line generates the highest revenue?
7. Which city generates the highest revenue?
8. Which product line has the highest VAT?
9. Which branches sell more products than the average quantity sold?
10. What is the most common product line purchased by each gender?
11. What is the average customer rating for each product line?

---

## Sales Analysis

1. How many sales are made during each time of the day for every weekday?
2. Which customer type generates the highest revenue?
3. Which city has the highest tax percentage?
4. Which customer type pays the highest VAT?

---

## Customer Analysis

1. How many unique customer types are present?
2. How many unique payment methods are used?
3. What is the most common customer type?
4. Which customer type purchases the most products?
5. What is the gender distribution of customers?
6. What is the gender distribution across each branch?
7. During which time of the day do customers give the highest ratings?
8. During which time of the day do customers give the highest ratings in each branch?
9. Which weekday has the highest average customer rating?
10. Which weekday has the highest average rating in each branch?

---

## Revenue and Profit Calculations

### 1. Cost of Goods Sold (COGS)

COGS represents the total cost of the products sold.

```text
COGS = Unit Price × Quantity
```

### 2. Value Added Tax (VAT)

VAT is the tax charged on the purchase.

```text
VAT = 5% × COGS
```

### 3. Total Revenue

The total amount paid by the customer is calculated as:

```text
Total = COGS + VAT
```

### 4. Gross Income

Gross income represents the profit earned after subtracting the cost of goods sold from total sales.

```text
Gross Income = Total Revenue - COGS
```

### 5. Gross Margin Percentage

Gross margin percentage shows the gross income earned as a percentage of total revenue.

```text
Gross Margin % = (Gross Income / Total Revenue) × 100
```

---

## Example Calculation

Consider the following transaction:

| Item | Value |
|---|---:|
| Unit Price | 45.79 |
| Quantity | 7 |
| VAT Rate | 5% |

### Step 1: Calculate COGS

```text
COGS = 45.79 × 7
     = 320.53
```

### Step 2: Calculate VAT

```text
VAT = 5% × 320.53
    = 16.0265
```

### Step 3: Calculate Total Revenue

```text
Total = 320.53 + 16.0265
      = 336.5565
```

### Step 4: Calculate Gross Income

```text
Gross Income = 336.5565 - 320.53
             = 16.0265
```

### Step 5: Calculate Gross Margin Percentage

```text
Gross Margin % = (16.0265 / 336.5565) × 100
               ≈ 4.7619%
```

---

## Database Setup

### Create Database

```sql
CREATE DATABASE IF NOT EXISTS salesDataWalmart;

USE salesDataWalmart;
```

### Create Table

```sql
CREATE TABLE IF NOT EXISTS sales(
    invoice_id VARCHAR(30) NOT NULL PRIMARY KEY,
    branch VARCHAR(5) NOT NULL,
    city VARCHAR(30) NOT NULL,
    customer_type VARCHAR(30) NOT NULL,
    gender VARCHAR(30) NOT NULL,
    product_line VARCHAR(100) NOT NULL,
    unit_price DECIMAL(10,2) NOT NULL,
    quantity INT NOT NULL,
    tax_pct FLOAT(6,4) NOT NULL,
    total DECIMAL(12,4) NOT NULL,
    date DATETIME NOT NULL,
    time TIME NOT NULL,
    payment VARCHAR(15) NOT NULL,
    cogs DECIMAL(10,2) NOT NULL,
    gross_margin_pct FLOAT(11,9),
    gross_income DECIMAL(12,4),
    rating FLOAT(2,1)
);
```

---

## Feature Engineering Queries

### Add Time of Day

```sql
ALTER TABLE sales ADD COLUMN time_of_day VARCHAR(20);
```

```sql

UPDATE sales 
SET 
    time_of_day = (CASE
        WHEN `time` BETWEEN '00:00:00' AND '12:00:00' THEN 'Morning'
        WHEN `time` BETWEEN '12:01:00' AND '16:00:00' THEN 'Afternoon'
        ELSE 'Evening'
    END);
```

### Add Day Name

```sql
ALTER TABLE sales ADD COLUMN day_name VARCHAR(10);
```

```sql
UPDATE sales 
SET 
    day_name = DAYNAME(date);
```

### Add Month Name

```sql
ALTER TABLE sales ADD COLUMN month_name VARCHAR(10);
```

```sql
UPDATE sales
SET
    month_name = MONTHNAME(date);
```

---

## Project Structure

```text
WalmartSalesAnalysis/
│
├── README.md
│
├── SQL_queries.sql
│
└── WalmartSalesData.csv
```

---

## SQL Queries

All SQL queries used for data exploration and analysis are available in the following file:

[SQL_queries.sql](SQL_queries.sql)

The SQL file contains queries for:

- Product analysis
- Sales analysis
- Customer analysis
- Revenue calculations
- Feature engineering
- Exploratory data analysis

---

## Key Skills Demonstrated

- SQL Database Creation
- Table Creation and Data Import
- Data Cleaning
- Data Wrangling
- Feature Engineering
- Aggregate Functions
- GROUP BY and ORDER BY
- CASE Statements
- Date and Time Functions
- Exploratory Data Analysis
- Business Problem Solving

---

## Conclusion

This Walmart Sales Data Analysis project demonstrates how SQL can be used to transform raw sales data into meaningful business insights.

By analyzing product performance, sales trends, branch revenue, and customer behavior, the project provides a practical understanding of how data analysis can support business decisions.

The project also helped strengthen SQL skills and build a foundation for future data analyst projects.

---

## Dataset Source

[Kaggle Walmart Sales Forecasting Competition](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting)
