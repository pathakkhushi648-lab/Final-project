Sales Performance Dashboard (Power BI Project)

Project Overview

This project is a Sales Performance Dashboard built using Power BI to analyze and visualize business data. The dashboard provides insights into sales, profit, customer behavior, product performance, and regional trends using interactive visuals and DAX calculations.


Objectives

* Analyze overall business performance
* Identify top-performing products and regions
* Track sales trends over time
* Monitor returns and customer behavior
* Enable interactive filtering and drill-through analysis


Dataset Description

The project uses a Star Schema Data Model.

Fact Tables

* Sales_fact stores transaction data (Sales, Quantity, etc.)
* Returns_fact stores returned product details

Dimension Tables

* Customer_Dim contains customer details (Name, Segment, Region)
* Product_Dim contains product details (Category, Price)
* Date_Dim contains date hierarchy (Year, Month, Quarter)
* Region_Dim contains region and manager information

Data Model Relationships

* Sales_fact → Customer_Dim (CustomerID)
* Sales_fact → Product_Dim (ProductID)
* Sales_fact → Date_Dim (DateID)
* Customer_Dim → Region_Dim (Region)
* Sales_fact → Returns_fact (SaleID)

Key Features of Dashboard

KPI Cards

* Total Sales
* Total Profit
* Profit Percentage
* Total Quantity
* Total Returns

Visualizations

* Sales Trend (Line Chart – Year and Month)
* Sales by Region (Bar Chart)
* Sales by Category (Donut Chart)
* Top 10 Products (Bar Chart)
* Matrix Table (Category → Product → Region)
* Return Analysis (Pie Chart)

Interactivity

* Slicers: Year, Month, Region, Category
* Drill-through: Product and Region details
* Dynamic filtering across all visuals

DAX Formulas Used

Base Measures


Total Sales = SUM(Sales_fact[TotalAmount])
Total Quantity = SUM(Sales_fact[UnitsSold])
Total Returns = COUNT(Returns_fact[ReturnID])


Profit Calculations

Total Profit = SUM(Sales_fact[TotalAmount]) * 0.2
Profit % = DIVIDE([Total Profit], [Total Sales], 0)


Time Intelligence

Year-over-Year (YoY)

Sales PY = CALCULATE([Total Sales], SAMEPERIODLASTYEAR(Date_Dim[Date]))

YoY % = 
DIVIDE(
    [Total Sales] - [Sales PY],
    [Sales PY],
    0
)


Month-over-Month (MoM)


Sales PM = CALCULATE([Total Sales], PREVIOUSMONTH(Date_Dim[Date]))

MoM % = 
DIVIDE(
    [Total Sales] - [Sales PM],
    [Sales PM],
    0
)


Year-To-Date (YTD)


Sales YTD = TOTALYTD([Total Sales], Date_Dim[Date])


Ranking and Top Products

Product Sales = SUM(Sales_fact[TotalAmount])

Product Rank = 
RANKX(
    ALL(Product_Dim[ProductName]),
    [Product Sales],
    ,
    DESC
)


Region Analysis

Region Sales = SUM(Sales_fact[TotalAmount])

Highest Region Sales =
MAXX(
    VALUES(Region_Dim[RegionName]),
    [Region Sales]
)


Insight Generation

Sales Insight = 
"Sales " & 
IF([YoY %] > 0, "increased", "decreased") &
" by " & 
FORMAT([YoY %], "0.00%") &
" compared to last year"

Dashboard Design

* Dark theme with consistent color palette
* KPI cards with highlighted metrics
* Clean layout with proper spacing
* Conditional formatting in matrix
* Data labels and titles for clarity


Advanced Features

* Drill-through pages for detailed analysis
* Conditional formatting in matrix
* Top N filtering (Top 10 products)
* Dynamic insights using DAX
* Interactive slicers

Mobile Optimization

* Dashboard optimized for mobile layout
* Key KPIs and charts arranged vertically

Key Insights

* Identified highest sales region
* Found top-performing products
* Analyzed monthly trends and growth
* Evaluated return reasons and patterns


Tools and Technologies

* Power BI Desktop
* DAX (Data Analysis Expressions)
* Excel Dataset


Project Deliverables

* Power BI file (.pbix)
* Dashboard visuals
* DAX formulas
* Documentation (README)

Learning Outcomes

* Understanding of data modeling (Star Schema)
* Hands-on experience with DAX
* Dashboard design and storytelling
* Business data analysis techniques


Conclusion

This project demonstrates how raw data can be transformed into meaningful insights using Power BI. It highlights key business metrics and supports decision-making through interactive visualizations.



Author
Swarna Ajay Pathak
