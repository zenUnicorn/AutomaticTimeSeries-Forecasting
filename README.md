# AutomaticTimeSeries-Forecasting (Auto-TS)
Auto-TS is a python package that is open-source and mostly used to automate time series forecasting. 
With just one line of code, it will automatically train various time series models, allowing us to select the most appropriate one for our issue statement. 
Auto-TS is a Python time series tool created for the purpose of quickly implementing accurate predictions at scale.

- Installation
```python
pip3 install auto-ts  OR
pip3 install autots
```

- Importing the libraries needed.
```python
import pandas as pd
import numpy as np

import matplotlib.pyplot as plt
from autots import AutoTS

```

- Data set (included in this repo)
```python
df = pd.read_csv("Apple-stock-data.csv")
df.head()
```

- Let's get more information about the dataset.
```python
df.info()
df.shape()
```

` Let's prepare the data first and have a look at Apple's closing stock prices before using the AutoTs library to do the task of stock price prediction:
```python
df = df[["Date", "Close"]]
df["Date"] = pd.to_datetime(df.Date)
df["Close"].plot(figsize=(12, 8), title="Apple Stock Prices", fontsize=20, label="Close Price")
plt.legend()
plt.grid()
plt.show()
```

- Let's now look at how to automate time series forecasting using the AutoTS library:
```python
from autots import AutoTS
model = AutoTS(forecast_length=7, frequency='infer', 
               ensemble='simple', drop_data_older_than_periods=200)
model = model.fit(data, date_col='Date', value_col='Close', id_col=None)
```

- Finally, let's use the predict function and examine the result:
```python
prediction = model.predict()
forecast = prediction.forecast
print(forecast)
```
