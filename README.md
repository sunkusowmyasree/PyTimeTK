# PyTimeTK
Time Series Analysis Package

# Introduction

Time series analysis is fundamental in many fields, from business forecasting to scientific research. While the Python ecosystem offers tools like pandas, they sometimes can be verbose and not optimized for all operations, especially for complex time-based aggregations and visualizations.

PytimeTK Offers blend of ease-of-use and computational efficiency and significantly simplifies the process of time series manipulation and visualization. By leveraging the polars backend, you can experience speed improvements ranging from 3X to a whopping 3500X which is a plus.

# Installation
Prerequisites - Make sure you have Python 3.9 or later installed on your system.
Install the latest stable version of pytimetk using pip: The Latest version is 0.2.0
`pip install pytimetk`

# PyTimeTK Basics
## Data Wrangling
Make use of below functions to perform data wrangling for timeseries using pytimetk
1. summarize_by_time - Summarize a DataFrame or Groupby Object by time. This function is helpful to perform aggregations on a dataset with groupby object over a time frequency. We can use multiple aggregation functions like ( Sum, Median, Minimum, Maximum, Standard deviation, Variance, First value in group, Last value in group, Count of values ,Number of unique values , Correlation between values, Custom lambda aggregating functions can be used too) on a dataframe with varied frequencies like ( such as “D” for daily or “MS” for month start, - S: secondly frequency - min: minute frequency - H: hourly frequency - D: daily frequency - W: weekly frequency - M: month end frequency - MS: month start frequency - Q: quarter end frequency - QS: quarter start frequency - Y: year end frequency - YS: year start frequency)
2. pad_by_time - Make Irregular time series regular by padding with missing data. For example if you have a month wise historical data which has few months missing then make use of pad_by_time and pad the missing data with null values.
3. future_frame - This function is used to extend a dataframe or Groupby object with future dates based on a specified length, optionally binding the original data.. This is mainly useful to prepare a future dataset which can be used for predictions.
## Data Visualization
1. plot_timeseries() - Creates time series plots using different plotting engines such as Plotnine, Matplotlib, and Plotly. 
## Anamoly Detection
Anomaly detection in time series analysis is a crucial process for identifying unusual patterns that deviate from expected behavior. These anomalies can signify critical, often unforeseen events in time series data. Effective anomaly detection helps in maintaining the quality and reliability of data, ensuring accurate forecasting and decision-making. The challenge lies in distinguishing between true anomalies and natural fluctuations, which demands sophisticated analytical techniques and a deep understanding of the underlying time series patterns. As a result, anomaly detection is an essential component of time series analysis, driving the proactive management of risks and opportunities in dynamic environments.

Anamoly Detection in pytimetk:
1. Anamolize - Detects anomalies in time series data, either for a single time series or for multiple time series grouped by a specific column.This function uses parallel processing to speed up computation for large datasets with many time series groups. Parallel processing has overhead and may not be faster on small datasets. To use parallel processing, set threads = -1 to use all available processors. This function returns a dataframe with below mentioned columns where recomposed_l1 and l2 are lower and upper level bound of recomposed time series.
2. Plot_Anomalies - Creates plot of anomalies in time series data using Plotly, Matplotlib.
3. Plot_Anomalies_decomp - This function takes in data from the anomalize() function, and returns a plot of the anomaly decomposition. It returns a plot of observed, seasonal and trends and remainder. We can make use of Groupby as well to plot it category wise.
4. Plot_Anomalies_cleaned - This function takes in data from the anomalize() function, and returns a plot of the anomalies cleaned which means we get to view the data before and after removing the anomalies 
## Feature Engineering
Adding Features to Time Series DataFrames (Augmenting) using below functions from pytimetk package
1. augment_timeseries_signature - Takes a DataFrame and a date column as input and returns the original df with the 29 different date and time based features added as new columns with the feature name based on the date_column.
2. augment_holiday_signature - Engineers 4 different holiday features from a single datetime for 137 countries.
3. augment_lags - Adds lags to a Pandas DataFrame or DataFrameGroupBy object.
4. augment_leads - Adds leads to a Pandas DataFrame or DataFrameGroupBy object.
5. augment_diffs - Adds differences to a Pandas DataFrame or DataFrameGroupBy object.
6. augment_rolling - Apply one or more Series-based rolling functions and window sizes to one or more columns of a DataFrame.
7. augment_rolling_apply - Apply one or more DataFrame-based rolling functions and window sizes to one
8. augment_expanding - Apply one or more Series-based expanding functions to one or more columns of a DataFrame.
9. augment_expanding_apply - Apply one or more DataFrame-based expanding functions to one or more columns of a DataFrame.
10. augment_fourier - Adds Fourier transforms to a Pandas DataFrame or DataFrameGroupBy object.
11. augment_hilbert - Apply the Hilbert transform to specified columns of a DataFrame.
12. augment_wavelet - Apply the Wavely transform to specified columns of a DataFrame.

## Comparision With Pandas

As evident from the table, pytimetk is not just about speed; it also simplifies your codebase. For example, summarize_by_time(), converts a 6-line, double for-loop routine in pandas into a concise 2-line operation. And with the polars engine, get results 13.4X faster than pandas!

Similarly, plot_timeseries() dramatically streamlines the plotting process, encapsulating what would typically require 16 lines of matplotlib code into a mere 2-line command in pytimetk, without sacrificing customization or quality. And with plotly and plotnine engines, you can create interactive plots and beautiful static visualizations with just a few lines of code.

For calendar features, pytimetk offers augment_timeseries_signature() which cuts down on over 30 lines of pandas dt extractions. For rolling features, pytimetk offers augment_rolling(), which is 10X to 3500X faster than pandas. It also offers pad_by_time() to fill gaps in your time series data, and anomalize() to detect and correct anomalies in your time series data.

## Conclusions
Through various pytimetk functions and techniques We can enhance our analytical approach on timeseries data.

Pytimetk features provide incredibly powerful techniques with a very easy strcuture and minimal code. They were indispensable in crafting a high-quality sales forecast, seamlessly integrated with sklearn.

This package offers a wide range of versatile time series functions, many of which can help improve Financial, Stock, Portfolio, and Investment Analysis in Python

All Augument related functions helps us to enrich our current dataset amd helps us in analysis througj lag and lead based feature and rolling calculations.

Gain valuable insights into our final model’s performance by leveraging plot_timeseries to visualize our results.
