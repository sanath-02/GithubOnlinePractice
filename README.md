# GithubOnlinePractice
import plotly.graph_objects as go
import pandas as pd
from google.colab import files
uploaded = files.upload()
df = pd.read_csv('Stock List.csv')

df = df.set_index(pd.DatetimeIndex(df['date'].values))

df
figure = go.Figure(
    data = [
            go.Ohlc(
                x = df.index,
                low = df['low'],
                high = df['high'],
                close = df['close'],
                open = df['open'],
                increasing_line_color = 'green',
                decreasing_line_color = 'red'
            )
    ]
)

#figure.update_layout(xaxis_rangeslider_visible = False)
figure.update_layout(
    title = 'Stock Price',
    yaxis_title = 'Stock Price($)',
    xaxis_title = 'Date'
)

figure.show()
