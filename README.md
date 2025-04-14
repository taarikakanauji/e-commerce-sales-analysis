# E-Commerce Sales Analysis - Power BI Report 

![BI Report](https://github.com/taarikakanauji/e-commerce-sales-analysis/raw/main/images/BI-Report.jpg)

## Problem Statement

Stakeholders across various departments lack a centralized, data-driven view to effectively monitor and analyze e-commerce sales across different regions, customer segments, product categories, and profit metrics. This gap makes it challenging to identify underperforming areas, assess sales performance, and make informed decisions based on key indicators such as revenue, profit margins, and product-level performance. There is a need for an interactive dashboard that provides actionable insights.

This dashboard helps stakeholders track and analyze e-commerce sales based on region, customer segment, product category, and profit contribution. It delivers data-driven insights to uncover trends, improve sales strategies, optimize inventory, and maximize profitability. The dashboard is designed for key stakeholders:

- E-commerce Executives & Sales Strategists

- Marketing & Product Teams

- Finance & Business Analysts

-  Category Owners

# Objective

- `Monitor Sales Performance in Real Time` by providing stakeholders with a real-time overview of total sales, total profits, time periods, and product categories to quickly identify high-performing and low-performing areas.

- `Track Profitability by Product and Segment` Analyze profits by product and customer segment to guide pricing strategies and business decisions that improve overall profitability.

- `Identify Sales Trends and Opportunities` Visualize patterns, and growth opportunities through interactive visuals, helping stakeholders make proactive, data-driven business decisions.

- `Reveal what works and what doesn't` by pinpointing products and segments which work well with respective shipping modes, and implementing targeted improvements.

## Key Questions

    Q : What are our total sales and profit across different time periods?

    Q : Which products or product categories are generating the most sales and profit?

    Q : How do sales and profit vary across customer segments (e.g., Consumer, Corporate, Home Office)?

    Q : What is the Year-over-Year (YoY) growth in sales and profit?

    Q : Which shipping modes are most frequently used, and how do they impact sales and profit?

    Q : What are the top and bottom performing products in terms of profit margins?

    Q : Are there any seasonal trends or patterns in sales across different products or segments?

## Steps followed 

As a Business Analyst for a leading e-commerce organization, I was tasked with developing an interactive report/dashboard to help stakeholders monitor sales performance, profit trends, and overall product sales activity across the product range. The goal was to provide actionable insights to improve sales strategy, operational efficiency in terms of shipping modes, and customer satisfaction. Below, I explain my step-by-step approach to designing this dashboard in Power BI:


- Step 1 : Load data into Power BI Desktop. The dataset is a csv file.

- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.

- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".

- Step 4 : After a thorough review and cleanup, we now have a data which contains no errors or empty values across columns — indicating a high-quality dataset ready for transformation and visualization.

- Step 5 : In the report view, under the view tab, default theme was selected.

- Step 6 : Creating KPI Cards for Key Metrics - To provide stakeholders with a clear summary, I created four KPI cards displaying high-level performance indicators as shown below. These KPIs offer a real-time snapshot of operational health, and help in making data-driven decisions quickly and effectively.

      Total Profit = SUM(Orders[Profit])

      Total sales = SUM(Orders[Sales])

      % of Returned orders = 
      VAR _total_orders = DISTINCTCOUNT(Orders[Order ID])
      VAR _return_orders = DISTINCTCOUNT(Returns[Order ID])
      VAR _percentage = 
      DIVIDE(_return_orders, _total_orders) 
      RETURN _percentage

      Sales PY = CALCULATE([Total sales], SAMEPERIODLASTYEAR('Date table'[Date]))

      % change of sales (PY) = DIVIDE( [Total sales] - [Sales PY], [Sales PY])

      Profit PY = CALCULATE([Total Profit],SAMEPERIODLASTYEAR('Date table'[Date]))

      % change of profit(PY) = DIVIDE([Total Profit] - [Profit PY],[Profit PY])

      % returned orders PY = CALCULATE([% of Returned orders], SAMEPERIODLASTYEAR( 'Date table'[Date]))

      % returned orders (PY) = [% of Returned orders] - [% returned orders PY]

   I formatted these cards with currency symbols and percentage representation to make trends easily understandable. These KPIs help executives quickly assess fundamental performance without diving into granular data.

  ![KPI](https://github.com/taarikakanauji/e-commerce-sales-analysis/raw/main/images/kpi.jpg)
           
- Step 7 : Representing the profit by each product - I added a bar chart to show how much profit was recorded for each of the products. 

        Fields Used:

        X-axis: Category, sub-category

        Y-axis: Total Profit

   The chart revealed the highest profit grossing products were copiers, accessories and phones, all falling under the Technology segment. The lowest profits were recorded for tables, bookcases and supplies. The furniture and office supplies segments were not as profitable compared to technology.

  ![Profit by Product](https://github.com/taarikakanauji/e-commerce-sales-analysis/raw/main/images/profit-product.jpg)

- Step 8 : Showcasing yearly sales vs. previous year sales - To better understand the evolving trends, I created a line chart showing the yearly sales, superimposed by the previous year sales.  

        Fields used:

        Y-Axis: Total Sales, sales PY

        X-axis: start of month

   The main purpose of this graph is to clearly understand the increase and decrease of sales observed between the years. This can highlight significant details related to how the trends are changing and what can be done to increase the sales in the coming time.

  ![Sales Over Time](https://github.com/taarikakanauji/e-commerce-sales-analysis/raw/main/images/sale-time.jpg)

- Step 9 : Categorizing sales recorded by shipping modes - As an e-commerce platform, it is crucial to observe the performance of shipping mode options provided by the platform. I created a simple bar chart to showcase the division of total sales based on shipping modes. 

        Fields used:

        Y-axis: Total Sales

        X-Axis: Shipping Mode (First class, Same day, Second class, Standard class)

  The highest sales were recorded under the Standard class shipping mode while the least were achieved for same day delivery. This indicates that customers are not ready to pay extra money for the same day deliveries and may use other shipping modes to keep the cost reasonable on their end.

  ![Sales by Ship Mode](https://github.com/taarikakanauji/e-commerce-sales-analysis/raw/main/images/sale-ship-mode.jpg)

- Step 10 : Total sales by segments - This pie chart is pretty simple and highlights the percentage division of sales between the segments. 

        Fields used:

        Legend: Segments (Home office, Corporate, Consumer)

        Values: Total sales

  The hero segment is the consumer segment, with a staggering sales of 50.32%. The home office and corporate segments collectively bring about 49% of sales and present an opportunity to further improve their sales, through innovative strategies and marketing.   

  [![Sales by Segment](https://github.com/taarikakanauji/e-commerce-sales-analysis/raw/main/images/sale-segment.jpg) 


- Step 11 : Adding Filters to the Dashboard – To improve the user experience, I added three slicers that allow users to filter the data according to their specific needs. These slicers are conveniently accessible via a filter icon located at the top of the dashboard.

  Configuring Slicers for Interactive Filtering – To enable users to interactively explore the report and focus on particular areas of interest, I set up slicers that dynamically filter the entire dashboard. These filters help users drill down into key dimensions for more targeted analysis.

  I added slicers for:

  `Customer name`

  `Country/Region`

  `Segment (Corporate, Home office, Consumer)`

  I chose dropdown-style slicers for a clean interface, ensuring they influence all report visuals. This allows business teams to filter data—for example, comparing the transaction frequencies in terms of various scenarios. 

  Additionally, I also added a date range filter to show the data for specific date ranges. This is extremely helpful when trying to understand the seasonal sales patterns, trends and how the sales fluctuate during certain times of the year.

  `Date from (dd/mm/yyyy) and date to (dd/mm/yyyy)`

  ![BI Report Filter](https://github.com/taarikakanauji/e-commerce-sales-analysis/raw/main/images/BI-Report-filter.jpg)


- Step 12 : Adding a Reset Filters Option – To enhance the usability and interactivity of the Power BI report, I integrated a Reset Filter icon that allows users to quickly clear all slicer selections and return the report to its original default state. This feature provides users with confidence and flexibility, eliminating concerns about making irreversible filter changes by reassuring them that any selections can be easily undone.

  First, Using the Insert > Image option, I added a reset or refresh icon. This icon was placed on the left side of the filter icon for visibility and ease of access.

  Then I cleared all slicer selections (Customer name, Country/Region, Segment and Date range). 

  I enabled Action on the reset filters icon by setting, Type- Bookmark and Bookmark- Clear all Filters. This ensures that when the icon is clicked, all slicers and filters return to their default (unselected) state.

# Snapshot of Report (Power BI Service)

  ![Service Report Full](https://github.com/taarikakanauji/e-commerce-sales-analysis/raw/main/images/Service-Report-full.jpg)
  

# Report Snapshot (Power BI DESKTOP)

  ![BI Report Full](https://github.com/taarikakanauji/e-commerce-sales-analysis/raw/main/images/BI-Report-full.jpg)

# **Project Resources**  

### **Detailed Report (PDF)**  
[Insights of E-Commerce Sales](https://github.com/taarikakanauji/e-commerce-sales-analysis/blob/main/Insights%20for%20E-Commerce%20Sales%20Report.pdf)  

### **Power BI Desktop Demo**  
[Power BI Demo (MKV)](https://github.com/taarikakanauji/e-commerce-sales-analysis/blob/main/Power-BI-Demo.mkv)  

### **Power BI Service Demo**  
[Power BI Service Demo (MKV)](https://github.com/taarikakanauji/e-commerce-sales-analysis/blob/main/Power-Service-Demo.mkv)  

### **Dataset Folder**  
[Dataset Files](https://github.com/taarikakanauji/e-commerce-sales-analysis/tree/main/dataset)  

### **PBIP Files**  
- **Report:** [Report Files](https://github.com/taarikakanauji/e-commerce-sales-analysis/tree/main/E-commerce%20Sales%20Report.Report)  
- **Semantic Model:** [Semantic Model Files](https://github.com/taarikakanauji/e-commerce-sales-analysis/tree/main/E-commerce%20Sales%20Report.SemanticModel)  
- **Project File:** [E-Commerce Sales PBIP](https://github.com/taarikakanauji/e-commerce-sales-analysis/blob/main/E-commerce%20Sales%20Report.pbip)  
- **Gitignore:** [.gitignore](https://github.com/taarikakanauji/e-commerce-sales-analysis/blob/main/.gitignore)  

### **Project README (Setup Guide)**  
[README.md](https://github.com/taarikakanauji/e-commerce-sales-analysis/blob/main/README.md)  

# Conclusion

This dashboard empowers stakeholders to:
- Identify crucial information related to E-commerce sales, profits and segments.
- Differentiate the products in terms of top performers and the bottom performer, and strategize to uplift the bottom performers.
- Optimize the strong segments and develop creative solutions to boost sales for the weaker segments

By leveraging these insights, the resources can be allocated more effectively to high-performing segments, underperforming areas can be identified and addressed proactively, and strategic decisions can be made with greater confidence. This data-driven approach empowers stakeholders to optimize operations, boost profitability, and enhance customer satisfaction. Ultimately, the dashboard serves as a centralized tool for continuous performance monitoring and improvement. It enables the organization to stay agile and competitive in a dynamic e-commerce landscape.  


