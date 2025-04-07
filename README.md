# Mean Reversion Trading Strategy on VWAP

This repository contains a proprietary trading strategy based on mean reversion using the Volume Weighted Average Price (VWAP). The project includes data processing, microstructure analysis, strategy implementation, and backtesting with critical reflections and proposed improvements.

This was part of FINS3666 at UNSW with Prof. Shane Miller. Work done by Rohan Phadke.

## Data Processing & Microstructure Analysis

- **Data Filtering:**  
  Filtered trades and limit order book data for Jan 15, 2025, from 10:10 AM to 4:00 PM (AEST).

- **Data Merging:**  
  Merged trades with the last order book snapshot before each trade.

- **Metrics Computed:**  
  - Bid-ask spread  
  - Common midprice

## Proprietary Trading Strategy

Inspired by observed fluctuations of PXA around VWAP, the strategy implements mean reversion:

- **Entry Criteria:**  
  - **Long:** Enter when the traded price drops 3+ cents below VWAP.  
  - **Short:** Enter when the traded price rises 3+ cents above VWAP.

- **Exit Criteria:**  
  - **Long Positions:**  
    - Take profit: 3 cents above entry price.  
    - Stop loss: 1 cent below entry price.  
  - **Short Positions:**  
    - Take profit: 3 cents below entry price.  
    - Stop loss: 1 cent above entry price.

- **Position Sizing:**  
  Each trade is set to 31 shares, determined by the average volume on Jan 15, 2025.

- **Trade Execution:**  
  Executes market orders by crossing the spread:  
  - Long entries at the ask price.  
  - Short entries at the bid price.

- **Position Management:**  
  Only one open position is allowed at a time.

## Backtesting & Performance Metrics

Backtesting on Jan 15, 2025 yielded the following metrics:

- **Total Amount Traded:** $56,045.83  
- **Total Profit:** -$71.61  
- **Percentage Return:** -0.13%  
- **Number of Trades:** 139  
- **Average Profit per Trade:** -$0.5152  
- **Win Rate:** 5.04%  
- **Max Profit on a Trade:** $1.24  
- **Max Loss on a Trade:** -$1.55  

*Analysis indicates that trading costs from crossing the spread eroded the expected small profits.*

## Critical Reflection & Future Improvements

- **Critical Reflection:**  
  - Trading costs eliminated the small profits anticipated.  
  - Simulations using the last traded price (instead of bid/ask) showed improved performance metrics.

- **Future Enhancements:**  
  - Evaluate bid/ask pressure using a Bayesian probabilistic model to predict price movements.  
  - Implement a dynamic stop-loss instead of a fixed one.  
  - Adjust position size based on market volatility rather than using a constant size.
