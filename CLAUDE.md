# Claude 角色設定

## 身份
你是一位前端工程師，負責為此專案建立網頁。

## 技術棧
- 純 HTML5 + Tailwind CSS（CDN）+ 原生 JavaScript
- 單一 `.html` 檔案，不使用任何框架
- 不依賴外部 JS 檔案（除 CDN）

## 預設風格
- 深色系、運動感
- 主色：`#7c6af7`（紫）
- 圓角卡片設計

## 輸出格式
- 輸出完整可執行的 HTML，不省略任何程式碼

> 若單次需求有特定覆蓋設定，以需求描述為準。

---

# 落地頁批量生成專案

## 專案目標

大量生成行銷落地頁，每頁針對不同關鍵字 / 受眾 / 活動，部署至 Netlify。

---

## 品牌資訊（必填）

```
品牌名稱：12EBT
品牌口號：Lead with Sincerity
品牌 Logo URL："C:\Users\adalyn.tzeng\Desktop\12bet-logo.png"

---

## 視覺規範

```

字型：             'Noto Sans TC', sans-serif  （根據每個需求的語言）
圓角：             8px
陰影：             0 4px 24px rgba(245,166,35,0.3)


> 需要更換色系時直接告訴 Claude，例如「改成紫金配色」。

---

## 產品線（勾選實際有的產品）

- [x] 真人荷官（Live Casino）— 百家樂、龍虎、輪盤
- [x] 體育投注（Sports Betting）— 足球、籃球、棒球
- [x] 老虎機（Slot Games）— PG、PP、JDB
- [x] 彩票（Lottery）— 六合彩、539、賓果
- [ ] 電子競技（Esports）
- [ ] 撲克（Poker）

---

## 目標市場

主要語言：越南文、泰文、英文、簡體中文  
目標地區：越南、泰國、印度、馬來西亞  
受眾年齡：25–45 歲男性  
裝置優先：**手機優先（Mobile First）**

---

## 技術規範

每個落地頁必須是 **單一完整可執行的 HTML 檔案**，規格如下：

```
- 技術：純 HTML5 + Tailwind CSS（CDN）+ 原生 JavaScript
- 不使用 React / Vue / 任何框架
- 不依賴外部 JS 檔案（除 CDN）
- 圖片：優先使用 Unsplash CDN 或 placehold.co 佔位
- 動畫：CSS animation 或輕量 JS，不引入 GSAP 等大型套件
- 必須在手機（375px）和桌機（1280px）都正常顯示
```

---

## 落地頁標準結構

每個落地頁依序包含以下區塊：

1. **頂部公告欄**：滾動跑馬燈，顯示活動文字
2. **Hero 區**：大標題 + 副標題 + CTA 按鈕（立即註冊 / 領取優惠）
3. **信任指標**：會員人數、出金速度、成立年份（數字動畫）
4. **主打優惠卡片**：3–4 張，各附圖示、標題、說明、按鈕
5. **產品展示**：遊戲截圖卡片輪播或網格
6. **步驟說明**：如何加入（3 步驟）
7. **客服浮動按鈕**：LINE / Telegram，固定在右下角
8. **頁尾**：免責聲明、版權

---

## 頁面類型與用途

| 類型代碼 | 用途 | 關鍵賣點 |
|----------|------|----------|
| `welcome` | 新會員歡迎頁 | 首存優惠、免費體驗金 |
| `sports` | 體育投注專頁 | 賠率高、即時串關 |
| `casino` | 真人娛樂場專頁 | 真人荷官、24h 不停 |
| `slot` | 老虎機專頁 | 高RTP、免費旋轉 |
| `vip` | VIP 會員招募頁 | 專屬禮遇、快速出金 |
| `promo` | 活動促銷頁 | 限時優惠、倒數計時 |
| `agent` | 代理招募頁 | 高佣金、被動收入 |

---

## Golden Prompt 公式

生成新落地頁時使用以下格式：

```
你是一位專業的線上博弈行銷網頁設計師。

請使用以下規格建立一個完整可執行的單頁 HTML：

【頁面類型】：[類型，例如：welcome / sports / promo]
【主題活動】：[例如：五月份首存送 100% / 世界盃特別版]
【主標題】：[例如：首存最高送 $3,000 彩金]
【CTA 連結】：[填入實際連結，或用 # 佔位]
【特殊需求】：[例如：加入倒數計時器 / 強調快速出金]

技術規範：純 HTML + Tailwind CSS CDN + 原生 JS，單一檔案，輸出完整程式碼不省略。
色系：主色 #F5A623，背景 #0F0F1A，文字白色。
語言：繁體中文，手機優先。
```

---

## 檔案命名規範

```
pages/
  welcome-01.html       # 新會員首頁 v1
  welcome-02.html       # 新會員首頁 v2（A/B 測試）
  sports-worldcup.html  # 體育投注世界盃版
  promo-may2026.html    # 五月活動頁
  vip-recruit.html      # VIP 招募頁
  agent-join.html       # 代理招募頁
```

---

## SEO 標準（每頁必含）

```html
<title>【品牌名】- 【頁面主題，20-60字元】</title>
<meta name="description" content="【120-160字元描述】">
<meta property="og:image" content="【1200x630px 圖片 URL】">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link rel="canonical" href="【此頁完整 URL】">
```

---

## 部署流程

```bash
# 單頁部署（拖曳）
# 將 pages/ 資料夾拖曳至 https://app.netlify.com/drop

# CLI 部署（需先設定 NETLIFY_AUTH_TOKEN）
netlify deploy --dir=pages --prod
```

---

## 常見修改指令（直接對 Claude 說）

- 「把 CTA 按鈕改成紅色閃爍效果」
- 「加入 LINE 客服浮動按鈕，ID 是 @xxxx」
- 「在 Hero 區加入倒數計時器，截止日期 2026-05-31」
- 「把所有按鈕文字改成『立即領取』」
- 「幫我做一個 A/B 版本，主標題改成強調快速出金」
- 「加入 Google Analytics，追蹤 ID：G-XXXXXXXX」
