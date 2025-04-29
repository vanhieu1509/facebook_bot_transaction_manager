
# Personal Finance Manager Chatbot using Facebook Messenger and Google Sheets

This Google Apps Script project is a lightweight personal finance manager chatbot. It integrates with Facebook Messenger to receive user messages, store and analyze financial transactions, and respond with reports via chat. All data is stored in Google Sheets for persistence.

## ✨ Features

- Add income and expenses using a simple message format.
- View monthly or weekly financial reports.
- Undo the most recent transaction.
- Reset all data in the current sheet.
- Automatically organizes transactions in monthly sheets.

## 🛠 Setup Instructions

### 1. Facebook Messenger Setup
- Create a Facebook Page and a Messenger App.
- Generate a Page Access Token and replace it in the script:
  ```js
  const PAGE_ACCESS_TOKEN = "insert_acess_token_pae";
  ```

- Set your webhook URL to your Apps Script `doPost` endpoint.
- Set the verify token to `thuchi`.

### 2. Google Sheet
- Create a Google Sheet and copy its ID into:
  ```js
  const SHEET_ID = "google sheet id";
  ```

- The sheet will automatically generate monthly sheets like `04/2025` when the first transaction is logged for the month.

### 3. Deploy Script as Web App
- Go to **Deploy > Manage deployments** in Apps Script.
- Select **Web App**, set "Execute as" to "Me", and access to "Anyone".
- Deploy the URL and use it as your Facebook Webhook.

## 📌 Usage Guide

Users interact with the bot by sending messages in the following formats:

### 1. Add Transaction
```
100k chi ăn trưa
```
or simply:
```
200k
```
(defaults to expense without "thu" or "chi")

### 2. View Report
```
/report
/report 04/2025
/report 28/04/2025
/report az
/report 03/2025 za
```

### 3. Undo Transaction
```
/undo
```

### 4. View Last Transaction
```
/last
```

### 5. Reset Sheet
```
/reset
```

### 6. Get Help
```
/start
```

## 📊 Data Format

Each monthly sheet has the following columns:

| Timestamp       | Type | Amount | Description      |
|----------------|------|--------|------------------|
| `DD/MM/YYYY HH:mm` | `thu` or `chi` | e.g., `100000` | e.g., `ăn trưa` |

## 📎 Notes

- Supports amount parsing with "k" and "tr" (e.g., `200k`, `2tr`).
- Automatically formats currency and sorts by amount on demand.
- Uses Apps Script’s `UrlFetchApp` to send replies to Messenger API.

## 📬 Contact

For improvements, bug reports, or enhancements, feel free to fork or open issues.
