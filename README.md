# Cryptocurrency Market Cap Visualization

This is a standalone web application that visualizes cryptocurrency market cap data using Chart.js. The application makes direct API calls to the CryptoCompare API and uses localStorage for caching.

## Features

- Visualizes market cap data for multiple cryptocurrencies (ADA, ETH, BNB, TON, SOL)
- Animates changes in market cap over time
- Caches API responses in localStorage to reduce API calls
- Works completely in the browser without requiring a backend server

## How to Use

1. Simply open the `index.html` file in your web browser.
2. The application will load and start fetching data from the CryptoCompare API.
3. Once data is loaded, the pie chart will be displayed and the animation will start.

For better performance and to avoid potential CORS issues, you can use any local web server of your choice to serve the HTML file.

## How It Works

1. **Direct API Calls**: The application makes direct calls to the CryptoCompare API to fetch historical price data.
2. **Data Processing**: The raw API data is processed to calculate market caps based on coin supply.
3. **localStorage Caching**: API responses are cached in localStorage to reduce API calls and improve performance.
4. **Visualization**: Chart.js is used to create an animated pie chart showing the relative market caps of different cryptocurrencies.

## Cache Management

- Data is cached in localStorage for 1 hour.
- A "Clear Cache" button is provided to manually clear the cache if needed.
- If localStorage quota is exceeded, the oldest cache entries will be automatically removed.

## Technical Details

### API Endpoint

The application uses the following CryptoCompare API endpoint:
```
https://min-api.cryptocompare.com/data/v2/histoday
```

### Parameters

- `fsym`: From Symbol (the cryptocurrency you want data for)
- `tsym`: To Symbol (the currency to display values in)
- `limit`: Number of data points to return
- `aggregate`: Data aggregation in days (1 = daily data)

### Cryptocurrency Configuration

The application uses a unified configuration object for cryptocurrencies that includes both supply data and brand colors:

```javascript
const coins = {
  'ADA': {
    color: '#0033ad',      // Cardano blue
    supply: 45000000000
  },
  'ETH': {
    color: '#3c3c3d',      // Ethereum dark gray
    supply: 120000000
  },
  'BNB': {
    color: '#f3ba2f',      // Binance yellow
    supply: 166801148
  },
  'TON': {
    color: '#0088CC',      // TonCoin blue
    supply: 5000000000
  },
  'SOL': {
    color: '#14f195',      // Solana green
    supply: 555000000
  },
  'USDT': {
    color: '#26a17b',      // Tether green
    supply: 83000000000
  },
  'BTC': {
    color: '#f7931a',      // Bitcoin orange
    supply: 21000000
  }
};
```

Market cap is calculated by multiplying the price by the total supply of each cryptocurrency.

## About the Application

This application was refactored from a previous implementation that used a Python/Flask backend. The current version:

1. Works completely in the browser without any backend dependencies
2. Makes direct API calls to CryptoCompare
3. Uses localStorage for efficient client-side caching
4. Includes a "Clear Cache" button for user convenience

## Browser Compatibility

This application should work in all modern browsers that support:
- ES6+ JavaScript
- localStorage API
- Fetch API
- Chart.js
