# Sales_Analysis Of a Hardware Store

## Table Of Contents 

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Recommendations](#recommendations)

### Project Overview 

---
 A Hardware company named "X", a major supplier of hardware peripherals, has experienced a sales decline noted by Sales Director Mr. Y. Identifying the root cause and pinpointing declining business areas is challenging due to the company's extensive branch network. This project aims to conduct data analysis on sales data to uncover insights into the downturn. By analyzing sales performance across locations and timeframes, actionable intelligence will be provided to help the management team formulate targeted strategies for business optimization
 
![Transaction](https://github.com/saidaAfroj/Sales_Analysis/assets/85706545/dbe06878-094a-4e4f-b67f-17e58b2787da)



### Instructions to setup mysql on your local computer

1. Follow step in this video to install mysql on your local computer https://www.youtube.com/watch?v=WuBcTJnIuzo

### Data Sources 
Sales Data: The primary dataset used for this analysis is the "sales_data.sql" file, containing detailed information about the company.

## Tools
- Sql - Data cleaning 
- Sql Server - Data Analysis
- Tableu - Data Analysis and creating reports

## Data Cleaning and preparation

In the initial data preparation phase, we performed the following tasks:

1. Data loading and inspection.
2. Handling missing values.
3. Data cleaning and formatting.

### Exploratory Data Analysis

EDA involved exploring the sales data to answer key questions, such as:

- Which location is having less sale ?
- Is there any particular product for which those specific areas are having less sale?
- Year by year analysis of sale
- Which year has most sell / what is the peak sale period

### Data Analysis 
find out which location has lowest sale by joining two tables, applying group by and displaying them descending order:

```sql
SELECT market_code, SUM(sales_amount) ,markets_name
 FROM 
sales.markets INNER JOIN
sales.transactions  ON
sales.markets.markets_code = sales.transactions.market_code
GROUP BY market_code, markets_name
ORDER BY 2 desc;
```
Show total revenue in year 2020

```sql
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r"
```
### Deep Insights after the analysis 
- Delhi emerges as the location with the lowest sales volume, exhibiting the least amount of sales activity.
- Bengaluru stands out as the location with the highest sales performance, showcasing robust sales figures compared to other regions.
- Analysis indicates that products categorized under the "Own Brand" label demonstrate superior sales performance compared to those categorized as "Distribution" products, suggesting a higher demand or preference among consumers for company-branded offerings.
- Over the period spanning from 2017 to 2020, it is notable that 2020 emerges as the pinnacle year in terms of sales revenue, showcasing the highest levels of sales activity during this timeframe.

### Recommendations 
Based on the analysis, we recommend the following actions:

- Targeted marketing campaigns for Delhi to boost sales.
- Allocate resources and optimize sales channels in Bengaluru.
- Enhance product development for the "Own Brand" line.
- Incorporate key learnings from 2020 peak sales into strategic planning for sustained growth.

### Limitations 
I had to remove all zero values from sales_quantity and sales_amount columns because they would have affected the accuracy of my conclusions from the analysis. There are still a few outliers even after the omissions but even then we can still see that there is a positive correlation between both.

### References 
[Stack Overflow](https://stack.com)

