# Created by Pranav Sai

import os
import time
import pandas_datareader as web
from winotify import Notification, audio
def find_prices(stocks):
    stock_prices=[]
    for stock in stocks:
        try:
            price=web.DataReader(stock,"yahoo").iloc[-1]["Adj Close"]
            print(stock+": "+str(price))
            stock_prices.append(price)
        except:
            print("Sorry, couldn't find stock for "+stock)

    print("\n")
    return stock_prices
            
def run(time1):
    global stocks
    while True:
        current_price=find_prices(stocks)
        time.sleep(time1)
        for i in range(len(stocks)):
            if current_price[i]>sell_prices[i]:
                n=Notification( app_id="Pranav Sai's Stock Alarm",
                                title="Stock Price Alert For "+stocks[i],
                                msg="{stocks[i]} has reached a price of {current_price[i]}. Do you want to sell?",
                                duration="long"
                              )
                n.add_actions(label="Go to Stock Broker", launch="https://www.tdameritrade.com/")
                n.set_audio(audio.LoopingAlarm6,loop=True)
                n.show()

            elif current_price[i]<buy_prices[i]:
                n=Notification(
                    app_id="Pranav Sai's Stock Alarm",
                    title="Stock Price Alert For "+stocks[i],
                    msg=f"{stocks[i]} has reached a price of {current_price[i]}. Do you want to buy?",
                    duration="long"
                )
                n.add_actions(label="Go to Stock Broker", launch="https://www.tdameritrade.com/")
                n.set_audio(audio.LoopingAlarm8,loop=True)
                n.show()

            time.sleep(1)






stocks=["FB","AAPL","AMZN","NFLX","GOOGL","MSFT"]
sell_prices=[250,200,3000,250,2500,300]
buy_prices=[150,125,2000,150,2000,225]


run(5)
