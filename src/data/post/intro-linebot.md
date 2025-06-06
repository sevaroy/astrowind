---
publishDate: 2025-06-25T00:00:00Z
author: AI Writer
title: 'LINE Bot 快速入門'
excerpt: 本文帶你從零開始建立 LINE Bot，包含申請帳號與撰寫簡單回覆程式。
image: https://images.unsplash.com/photo-1603791440384-56cd371ee9a7?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80
category: Tutorials
tags:
  - linebot
  - messaging-api
  - tutorial
metadata:
  canonical: https://astrowind.vercel.app/intro-linebot
---

LINE 是台灣及日本常用的通訊軟體，透過 Messaging API 可以輕鬆打造自動化聊天機器人。以下將示範建立 LINE Bot 的基本步驟。

## 1. 建立 LINE 官方帳號

在 [LINE Developers](https://developers.line.biz/) 控制台建立 provider 與 channel，取得 `Channel Secret` 與 `Channel Access Token`，這些資訊稍後將用於驗證及呼叫 API。

## 2. 設定 Webhook

在雲端或本地伺服器架設一個可接收 POST 請求的端點，URL 填入 LINE 的 Webhook。以 Node.js 為例，可使用下列程式碼：

```javascript
app.post('/webhook', (req, res) => {
  const events = req.body.events;
  // 在此處理事件
  res.send('ok');
});
```

## 3. 回覆訊息

收到使用者傳來的事件後，可使用 Messaging API 回覆文字或圖片。以下以 reply API 為例：

```javascript
import { Client } from '@line/bot-sdk';

const client = new Client({ channelAccessToken });
client.replyMessage(event.replyToken, {
  type: 'text',
  text: 'Hello LINE Bot!',
});
```

## 結語

LINE Bot 不僅能自動處理客服，亦可整合第三方服務打造更多互動體驗。推薦進一步閱讀官方文件，探索更進階的功能。
