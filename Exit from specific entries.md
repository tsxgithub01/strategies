
> 策略名称

Exit from specific entries

> 策略作者

Zer3192





> 源码 (PineScript)

``` javascript
//@version=4
strategy(title="Exit from specific entries", overlay=true,
     pyramiding=2, close_entries_rule="ANY")

// Determine trading conditions
newDay = (dayofmonth != dayofmonth[1])

firstEntry  = newDay and (dayofweek == dayofweek.monday)
secondEntry = newDay and (dayofweek == dayofweek.tuesday)

firstExit  = newDay and (dayofweek == dayofweek.thursday)
secondExit = newDay and (dayofweek == dayofweek.friday)

// Submit entry orders
if (firstEntry)
    strategy.entry(id="EL 1", long=true)

if (secondEntry)
    strategy.entry(id="EL 2", long=true)

// Generate exit orders
if (firstExit)
    strategy.close(id="EL 2")

if (secondExit)
    strategy.close(id="EL 1")
```

> 策略出处

https://www.fmz.com/strategy/395966

> 更新时间

2023-01-07 21:20:36
