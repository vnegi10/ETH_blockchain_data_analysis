# Ethereum transaction data analysis

## Overview

This repository contains a Jupyter Notebook that analyzes Ethereum blockchain
transaction data using Python. The notebook is designed to help users understand
various aspects of transactions on the Ethereum network, including their value,
gas usage and execution status.

## Motivation

- **Educational Purpose:** To provide insights into how Ethereum transactions work and
how they can be analyzed programmatically
- **Practical Application:** To demonstrate the use of Python libraries such as
[Polars](https://pola.rs/) for working with blockchain data, which can be applied in
various projects related to decentralized finance (DeFi), smart contracts or
blockchain analytics.

## Content

The notebook covers the following topics:

- Data Loading: Lazy loading and preprocessing Ethereum block and transaction data
- Exploratory Data Analysis (EDA): Calculating key metrics such as total transaction
value per block, gas usage and number of transactions.
- Gas Cost Analysis: Analyzing the cost associated with transactions in terms of gas
price and used gas per block

## Data source

The blockchain data was extracted into parquet files using the Rust-based
[cryo](https://github.com/paradigmxyz/cryo) tool in combination with the web3 API
provided by [Ankr.](https://www.ankr.com/docs/) Note that an account needs to be
created even if you intend to make use of the limited capabilities under the freemium
pricing model.

Sample command for using cryo is shown below. It can take long (~ 2 hours) to complete
since we need to stay below the rate limit of 30 reqs/min. Also, we are fetching every
25th block, which means the data has a resolution of 5 minutes
(25 x 12 s (average time for each block) = 300 seconds).

```
cryo blocks_and_transactions --rpc https://rpc.ankr.com/eth/<YOUR_API_KEY> 
--blocks 14328824:16920824:25 --chunk-size 5000 --max-concurrent-requests 16
--requests-per-second 30 --output-dir your_dir
```

## Data coverage

Latest time range:

```
get_time_range()

| min_timestamp | max_timestamp |
| ------------- | ------------- |
| 2022-03-05 19:36:27 | 2025-03-22 20:26:35 |
```