<h1 style="text-align: center;">Online Retail Analysis
</h1>  
<a href="#"><img src="online-shopping-vs-in-store-shopping-1024x614.jpg" width="700" height="300" alt="descriptive text" /></a>


### INTRODUCTION
Utilizing Microsoft Excel, an indispensable and frequently demanded skill for the Data Analyst role, I adeptly manage to clean and manipulate raw datasets while also creating interactive dashboards. However, due to the dataset's size of over half a million rows, I encounter lags and delays. Consequently, for enhanced efficiency when analyzing large volumes of data, it is preferable to utilize other tools for convenience. 

<br />

### DATA COLLECTION
For this project, I used the dataset from this source: [Online Retail Dataset](https://archive.ics.uci.edu/dataset/352/online+retail),  which contains all the transactions occurring between 12/1/2010 to 12/9/2011 from a company that mainly sells unique all-occasion gifts. The dataset is based in the United Kingdom and registered non-store online retail. The raw dataset has 541,909 instances, and 6 features. 
<br />

<a href="#"><img src="raw data.png" width="700" height="450" alt="descriptive text" /></a>
<br />
<span style="color: rgba(0, 0, 0, 0.2);">Raw Data</span>

<br />

### DATA PREPARATION
The dataset is substantial, comprising over half a million rows, making it challenging to analyze. Initially, I copied the raw dataset, created a new sheet labeled 'Working Sheet,' and pasted it there. Within my Working Sheet, my first step was to check for duplicates in the raw data. By highlighting the relevant cells and navigating to the Data Tab, I successfully removed duplicates, resulting in the deletion of 5268 rows.
<br />

<a href="#"><img src="removing duplicates.png" width="850" height="450" alt="descriptive text" /></a>
<br />
<span style="color: rgba(0, 0, 0, 0.2);">Removing Duplicates</span>


<br />
After removing duplicates, my next step is to check for blank values using the Sort and Filter function. Upon filtering the description column, I noticed the presence of "?" values and blanks, prompting me to filter them out entirely. Upon further inspection, I discovered that all values in the price column were 0. Consequently, I made the decision to delete all rows containing such values for my analysis.
<br />
<br />
<a href="#"><img src="like values with question mark and blanks.png" width="600" height="375" alt="descriptive text" /></a>
<br />
<span style="color: rgba(0, 0, 0, 0.2);">Values with "?" like, and Blanks</span>

<br />
<br />
<br />
<a href="#"><img src="zero price.png" width="600" height="300" alt="descriptive text" /></a>
<br />
<span style="color: rgba(0, 0, 0, 0.2);">0 Price</span>

<br />


### DATA MANIPULATION & ANALYSIS
The next step involves navigating to the Insert Tab, allowing me to create a table that includes data from all the necessary cells for further analysis.
<br />
<br />
<a href="#"><img src="create table.png" width="750" height="225" alt="descriptive text" /></a>
<br />
<span style="color: rgba(0, 0, 0, 0.2);">Creating Table</span>
<br />
<br />

Upon checking the feature quantity filter, I discovered that some entries have negative quantity values. However, upon analyzing, I realized that these negative numbers may represent items that were likely removed due to expiration or the end of a promotion. Therefore, I decided to retain these instances of negative quantity for further analysis.
<a href="#"><img src="negative quantity.png" width="750" height="225" alt="descriptive text" /></a>
<br />
<span style="color: rgba(0, 0, 0, 0.2);">Negative Quantity</span>
<br />
<br />

There are 6 questions I will answer here:
1. How is our overall revenue performance to date?
2. What is the revenue performance of items sold as box sets?
3. What is the revenue performance of items sold as individual pieces (holder items)?
4. How many purchases originate from outside the UK?
5. Can we identify any instances of revenue loss?
6. What are the top 10 items by description in terms of revenue?
<br />

To address this, I must add six features to my Working Sheet, namely: Year, Month, Holder Item, Sold by Box, Quantity Status, and Revenue.

I will extract the Year and Month from the InvoiceDate feature using the TEXT function. The Holder Item feature will have 'Yes' or 'No' values, determined by this formula: "=IF(IFERROR(SEARCH("holder",C2), "not holder") = "not holder", "No", "Yes")". This formula searches for words similar to 'holder' within each Description value. If it finds the word 'holder', it returns 'Yes'; otherwise, it returns 'No'. The same logic applies to the Sold by Box feature.

For the Quantity Status feature, cells will display either 'Positive' or 'Negative' based on this formula: =IF([@Quantity]<0, "Negative", IF([@Quantity]>0,"Positive")).

I've added these features to enable us to assess revenue losses by using them as filters in our dashboard. Additionally, we can evaluate the total revenue with no loss. We can also identify the bottom 10 items by Description that have negative total revenue.

The Revenue feature is simply the product of the Quantity and UnitPrice features. 
<br />
<a href="#"><img src="added_features.png" width="600" height="200" alt="descriptive text" /></a>
<br />
<span style="color: rgba(0, 0, 0, 0.2);">Added Features</span>
<br />
<br />
### DATA VISUALIZATION
In these steps, I will create some pivot tables and an interactive dashboard. This process is inspired by a YouTuber named Mo Chen. You can watch the video by clicking the image below.
<br />
<div align="left"> 
      <a href="https://www.youtube.com/watch?v=m13o5aqeCbM">
         <img src="https://i.ytimg.com/vi/m13o5aqeCbM/hq720.jpg" style="width:25% height:25%;">
      </a>
</div>
<br />


### PIVOT TABLE
I will first create two sheets, namely: Pivot Table and Dashboard. In the Pivot Table sheet, I will proceed to create a pivot table by clicking on the Insert Tab, then selecting the PivotTable icon. Next, I will select all the cells in my Working Sheet.

To address the first question, I will choose 'Month' for Rows and 'Sum of Revenue' for Values from the PivotTable Field. Following this, I will insert a line chart, rename all axes, and customize the number category.

