
### Name: A.sasidharan
### Register no: 212221240049
### Date: 
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION



### AIM:
To Illustrates how to perform time series analysis and decomposition for electricity production

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:


~~~
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

df = pd.read_csv('/globaltemper.csv')
print(df.head())

# Assuming 'dt' is your date column and 'AverageTemperature' is your temperature data column
date_column_name = 'dt'  
temp_column_name = 'AverageTemperature'

# Changed date format to '%d-%m-%Y' to match the format in the CSV file
df[date_column_name] = pd.to_datetime(df[date_column_name], format='%d-%m-%Y')
df.set_index(date_column_name, inplace=True)
print(df.info())

plt.figure(figsize=(12, 6))
plt.plot(df[temp_column_name], label='Global Temperature', color='blue')  # Plot temperature
plt.title('Global Temperature Over Time')
plt.xlabel('Date')
plt.ylabel('Average Temperature')
plt.legend()
plt.show()

# Decompose the temperature data
decomposition = seasonal_decompose(df[temp_column_name], model='additive')
seasonal = decomposition.seasonal
plt.figure(figsize=(12, 6))
plt.plot(seasonal, label='Seasonal Component', color='green')
plt.title('Seasonal Component of Global Temperature')
plt.xlabel('Date')
plt.ylabel('Seasonal Effect')
plt.legend()
plt.show()

trend = decomposition.trend
plt.figure(figsize=(12, 6))
plt.plot(trend, label='Trend Component', color='orange')
plt.title('Trend Component of Global Temperature')
plt.xlabel('Date')
plt.ylabel('Trend Effect')
plt.legend()
plt.show()

plt.subplot(4, 1, 4)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.title('Over All Component')
plt.legend()

plt.tight_layout()
plt.savefig('decomposition_plots.png')  # Save decomposition plots as an image
plt.show()
~~~














### OUTPUT:
FIRST FIVE ROWS:

![image](https://github.com/user-attachments/assets/9dc3048c-d443-4fb1-84dc-ff448fefbe3c)




PLOTTING THE DATA:


![image](https://github.com/user-attachments/assets/0ff78cca-78d3-425c-a1c3-b4984f1294b0)


SEASONAL PLOT REPRESENTATION :


![image](https://github.com/user-attachments/assets/955ff719-784a-47ae-8e88-a2ad4d5bf549)





TREND PLOT REPRESENTATION :


![image](https://github.com/user-attachments/assets/48699c9f-c7b1-4dda-9135-f6f0b36f1d45)



OVERAL REPRESENTATION:


![image](https://github.com/user-attachments/assets/94295389-2bf6-4f29-96f6-cb419bbda64c)




### RESULT:
Thus a python code has been successfully executed for  time series analysis and decomposition of electricity production data.
