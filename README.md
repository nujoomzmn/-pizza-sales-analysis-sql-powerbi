# Pizza Sales Analysis - SQL & Power BI Dashboard

## 📊 Project Overview
This project analyzes pizza sales data to uncover business insights and performance metrics using **SQL for data querying**, **Power Query for data transformation**, and **Power BI for visualization**. The analysis covers key performance indicators, sales trends, and product performance across multiple dimensions.

## 🛠️ Technologies Used
- **SQL Server** - Data querying and analysis
- **Power BI** - Data visualization and dashboard creation
- **Power Query (M Language)** - Data transformation and cleaning
- **DAX (Data Analysis Expressions)** - Calculated measures and columns
- **Excel/CSV** - Data source management

## 📁 Dataset Structure
The `pizza_sales` table contains the following columns:
- **order_id** - Unique identifier for each order
- **order_date** & **order_time** - Date and time of order
- **pizza_id** & **pizza_name_id** - Pizza identifiers
- **pizza_name** - Name of the pizza
- **pizza_category** - Category (Classic, Supreme, Chicken, Veggie)
- **pizza_size** - Size (XX-Large, X-Large, Large, Medium, Regular)
- **pizza_ingredients** - List of ingredients
- **quantity** - Number of pizzas in the order
- **unit_price** - Price per pizza
- **total_price** - Total price for the line item

## 📈 Key Performance Indicators (KPIs)

### Financial Metrics
- **Total Revenue**: $817,860
- **Average Order Value**: $38.31
- **Total Pizzas Sold**: 49,574
- **Total Orders**: 21,350
- **Average Pizzas Per Order**: 2.32

## 📊 Business Insights

### 🕒 Temporal Trends
**Daily Patterns:**
- Peak sales on **Fridays and Saturdays** (evenings)
- Highest order volume: **Friday** (~3.5K orders)

**Monthly Trends:**
- Maximum orders in **July** (peak summer month)
- Second highest in **January** (post-holiday period)

### 🍕 Category Performance
**Sales Contribution by Category:**
1. **Classic**: 26.91% - Highest selling category
2. **Supreme**: 25.46%
3. **Chicken**: 25.44%
4. **Veggie**: 23.6%

**Size Preference:**
- **Large** pizzas dominate with 45.89% of sales
- **Medium** at 30.49%
- **XX-Large** has minimal contribution (0.12%)

## 🏆 Product Performance Analysis

### Top Performers
**By Revenue:**
1. **Thai Chicken Pizza** - Highest revenue generator
2. (Other top performers from SQL queries)

**By Quantity Sold:**
1. **Classic Deluxe Pizza** - Most units sold
2. (Other top performers from SQL queries)

**By Order Frequency:**
1. **Classic Deluxe Pizza** - Most frequently ordered

### Underperformers
**Worst by Revenue/Quantity/Orders:**
- **Brie Carre Pizza** - Lowest performance across all metrics

## 🔍 SQL Analysis Queries

### KPI Calculations
```sql
-- Total Revenue
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;

-- Average Order Value
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value 
FROM pizza_sales;

-- Total Pizzas Sold
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales;

-- Total Orders
SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales;

-- Average Pizzas Per Order
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
       CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
       AS Avg_Pizzas_per_order
FROM pizza_sales;

