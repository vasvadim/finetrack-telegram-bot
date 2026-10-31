<h1 align="center">📈 FineTrackBot</h1>

<p align="center">
  A Telegram bot that tracks Moscow Exchange (MOEX) stock prices for you: watch-list, live quotes, price charts, periodic checks and a correlation matrix of the tickers you follow.
</p>

<p align="center">
  <img alt="Python" src="https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white">
  <img alt="python-telegram-bot" src="https://img.shields.io/badge/python--telegram--bot-async-26A5E4?logo=telegram&logoColor=white">
  <img alt="MOEX ISS" src="https://img.shields.io/badge/data-MOEX%20ISS%20API-red">
  <img alt="pandas" src="https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white">
</p>

## Commands

| Command | What it does |
|---|---|
| `/start` | greeting and help |
| `/add` | add one or more tickers (e.g. `SBER GAZP YNDX`) to your watch-list |
| `/delete` | remove tickers from the watch-list |
| `/clear` | clear the watch-list |
| `/price` | current price of a ticker from the MOEX ISS API (TQBR board) |
| `/check` | start periodic price checks for the tracked tickers |
| `/plot` | price-history chart for a ticker (matplotlib) |
| `/corr` | correlation heat-map of standardised price series of all tracked tickers (seaborn) |
| `/cancel` | cancel the current dialogue |

Prices are fetched from `https://iss.moex.com/iss/engines/stock/markets/shares/boards/TQBR/securities.json` and appended to a rolling `data.csv` (ticker, price, timestamp), which feeds the charts and the correlation matrix.

## Run

```bash
git clone https://github.com/vasvadim/FineTrackBot.git
cd FineTrackBot
pip install python-telegram-bot aiohttp requests beautifulsoup4 pandas numpy matplotlib seaborn python-dotenv certifi
echo "API_KEY=<your Telegram bot token>" > .env
python main.py
```

## Repository

| Path | Contents |
|---|---|
| `main.py` | bot: command handlers, conversation flow, MOEX client, CSV storage, plotting |
| `data.csv` | rolling price log written by the bot |

---

<p align="center"><a href="https://github.com/vasvadim">Vadim Vasilenko</a> · 2025</p>
