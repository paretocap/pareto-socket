## pareto-socket

Combines public crypto currency websocket APIs to provide a low-resource, zero-configuration ticker. Each exchange, except for Bittrex, uses a real-time websocket.


### Supported exchanges

 - Bittrex
 - Bitstamp
 - Poloniex
 - GDAX
 - Gemini
 - CEX
 - Bitfinex
 - OKCoin
 - Bitmex

### Quickstart


```
cryptoSocket = require("crypto-socket")
cryptoSocket.start();

```

3) Get ticker quotes via **cryptoSocket.echoExchange()** or access object variable **cryptoSocket.Exchanges**

## Basic functions

### cryptoSocket.start(exchange,symbol)

Starts a websocket. Where ***exchange*** is always lowercase and ***symbol*** is always upper-case.



```
// listen to ETHBTC on bitfinex,bitmex,and cex.
cryptoSocket.start("bitfinex","ETHBTC")
cryptoSocket.start("bitmex","ETHBTC")
cryptoSocket.start("cex","ETHBTC")
```


### Supported for bitfinex and bittrex

Pass an array to subscribe to multiple markets

```
cryptoSocket.start("bitfinex",['LTCBTC','BTCUSD'])
```
These exchanges should support all markets that they have, and will be simple to add more.

**Note**

As of now, **Poloniex** exchange only has one open socket that sends back all data. The above syntax is not recommeneded unless you are only following one symbol, as it will open up multiple sockets that returns all data, and filter out your selections.
__________

### echoExchange()

A simple printout of all opened ticker quotes.



```
// print out quotes every 1000 ms (1 second)
setInterval(
	function(){
		cryptoSocket.echoExchange()
	},1000);
```

________________
### cryptoSocket.Exchanges

Access to the raw variable the module uses to store ticker quotes as they update. One value at a time.



```
// get bitfinex quotes
console.log(cryptoSocket.Exchanges['bitfinex'])
// renders '{ ETHBTC: 0.02492 }' to console.
```
