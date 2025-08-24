# Google Stock Price Analysis   

This project analyzes **Google (GOOG) stock price data** from **2004-08-19 onward** using Python, Pandas, and Matplotlib. The dataset contains daily trading information such as opening price, closing price, volume, and adjusted close values.  

 Dataset Description  
The dataset contains the following columns:  
- **Date** – Trading date  
- **Open** – Stock price at market open  
- **High** – Highest price of the day  
- **Low** – Lowest price of the day  
- **Close** – Stock price at market close  
- **Adj Close** – Adjusted closing price (accounts for splits & dividends)  
- **Volume** – Total number of shares traded  

##  Key Steps in Analysis  

1. **Data Preprocessing**  
   - Converted `Date` column into `datetime` format.  
   - Extracted new columns for **Year**, **Month Name**, and **Quarter** to enable time-based analysis.  

2. **Yearly Analysis**  
   ```python
   yearly_analysis = df.groupby('year').agg(
       max_open = ('Open', 'max'),
       max_close = ('Close', 'max'),
       avg_close = ('Close', 'mean'),
       total_volume = ('Volume', 'sum')
   ).reset_index()

   yearly_analysis.set_index('year')
   ```
   - Maximum Open & Close price per year  
   - Average Closing price per year  
   - Total Volume traded per year  

3. **Visualization**  
   - **Yearly Open & Close Price Trends** (Line Chart)  
   - **Last 3 Years Closing Price Trend** to observe patterns  
   - **Yearly Opening Price Trend**  
     ```python
     df.groupby('year')['Open'].mean().plot()
     ```  
   - **Monthly Opening Price Trend** (sorted by highest average)  
     ```python
     df.groupby('month_name')['Open'].mean().sort_values(ascending=False).plot()
     ```  
   - **Quarterly Opening Price Trend (Bar Chart)**  
     ```python
     df.groupby('quarter')['Open'].mean().plot(kind='bar')
     ```

4. **Yearly Returns**  
   - Example Calculation:  
     - **2005 → +104.7% return** (Stock more than doubled)  
     - **2008 → -55.1% return** (Global Financial Crisis impact)  

Insights  
- Google’s stock showed **massive growth in early years (2004–2005)**.  
- **2008** was the worst-performing year due to the financial crisis.  
- Seasonal/Quarterly trends help identify periods of strong performance.  

 Requirements  
- Python 3.x  
- pandas  
- matplotlib / seaborn  
- jupyter notebook / google cloud 

