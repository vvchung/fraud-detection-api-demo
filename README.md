# 🛡️ 詐欺交易預測 Demo：Flask API + 機器學習模擬資料

這是一個展示型的專案，示範如何從機器學習模型訓練、建立 API 到透過 Google Colab 與 ngrok 發布預測服務。

---

## 📦 專案內容

- 模擬詐欺金融交易資料集
- 訓練 Logistic Regression 模型
- 建立 Flask API 接收交易資料
- 使用 ngrok 實現線上測試（無需部署伺服器）

---

## 🚀 快速開始（Colab 上執行）

點選下方按鈕，在 Colab 開啟範例 Notebook：

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vvchung/fraud-detection-api-demo/blob/main/fraud_detection_api_demo.ipynb)

---

## 🧪 API Demo 測試方式

### 1. 啟動 Flask API

執行 Notebook 中 `app.run()` 相關區段，系統會自動透過 ngrok 建立公開 URL，例如：

```
 * Running on http://127.0.0.1:5000
 * ngrok tunnel "https://abc1234.ngrok.io"
```

請記下 ngrok 產生的 URL（例如 `https://abc1234.ngrok.io`）

---

### 2. 使用 curl 或 Python 測試 API

```bash
curl -X POST https://abc1234.ngrok.io/predict \
  -H "Content-Type: application/json" \
  -d '{
        "amount": 5000,
        "location": "台中",
        "device_type": "mobile",
        "time": 2.5
      }'
```

或使用 Python 測試：

```python
import requests

url = "https://abc1234.ngrok.io/predict"
data = {
    "amount": 5000,
    "location": "台中",
    "device_type": "mobile",
    "time": 2.5
}
res = requests.post(url, json=data)
print(res.json())
```

---

## 📊 輸出結果範例

```json
{
  "is_fraud": 1,
  "fraud_probability": 0.9342
}
```

---

## 📎 需求套件

- Python 3.8+
- Flask
- flask-ngrok
- pandas / numpy / scikit-learn / joblib

Colab 環境會自動安裝所需套件，無需手動設定。

---

## 📬 聯絡作者

由 [@vvchung](https://github.com/vvchung) 發布，用於教育與研究展示用途。
