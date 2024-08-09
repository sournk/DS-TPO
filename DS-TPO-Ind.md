# Индикатор DS-TPO

Индикатор копирует функции индикатора Time Price Opportunity (TPO) от TradingView. 
Подробное описание [тут](https://ru.tradingview.com/support/solutions/43000713306/).

### Автоматический расчет RowSize

When the "Row Size" input uses the "Auto" option, the indicator calculates the row size based on the latest 300 bars as of the rightmost visible bar. It first divides the difference between the highest high and lowest low across those bars by the symbol's minimum tick value:

`MinTickRange = (HighValue - LowValue) / MinimumTick`

Then, it divides this value by 80, i.e., the number of rows that must fit on the chart:

`RowTicks = MinTickRange / RowsRequired`

Lastly, it rounds the result to calculate the final ticks per row value:

`TicksPerRow = round(RowTicks / Increment) * Increment`

The increment it rounds to depends on the scale of the calculated value:

If 1 <= RowTicks <= 100, Increment = 5 If 100 <= RowTicks <= 1000, Increment = 50 If 1000 <= RowTicks <= 10000, Increment = 500 If 10000 <= RowTicks <= 100000, Increment = 5000 etc...

