# 崎山先生のおたからSHOP

超通信ストアのコードを土台に作った、まったく別のECサイトです。
崎山先生が見つけてきた「おたから」を販売しているサイト、という設定です。

## 構成（元サイトと同じ）
- 静的フロント（HTML/CSS/JS）→ Netlifyに公開
- Node/Expressサーバー（server.js）→ Renderに公開
- 決済: Stripe Checkout
- 商品データ: products.json

## 商品（3点）
1. チェルシー / 10,000円
2. M＆M'S ピーナッツ / 5,000円
3. ゴジラのぬいぐるみ / 20,000円

## デザイン
海賊の宝の地図・年季の入った紙のイメージ。
茶色メイン（背景 #d9c096、濃茶 #4a2f1b）、アクセントは赤（#a31621）。
見出しフォントは Kaisei Decol、本文は Noto Serif JP。
トップ画像（images/header.jpg）は宝の地図のイラスト（赤い×印・宝箱・羅針盤・錨）。

## 画像について
- 商品画像3点は本物の商品写真に差し替え済み（2026-11-17）。
- images/chelsea.jpg（チェルシー）
- images/mms-peanuts.jpg（M＆M'S ピーナッツ）
- images/godzilla.jpg（ゴジラのぬいぐるみ）

## 公開前にやること（公開直前の設定）
1. Netlifyで新しいサイトを作り、このフォルダのフロント部分を公開する
2. Renderで新しいWeb Serviceを作り、server.js を公開する
3. Renderの環境変数に設定する:
- STRIPE_SECRET_KEY = 新しいお店用のStripe秘密鍵（チャット等に貼らないこと）
- FRONTEND_URL = 手順1で決まったNetlifyのURL（例: https://xxxxx.netlify.app）
4. checkout.js の先頭にある SERVER_URL を、手順2のRenderのURLに書き換える
5. 特商法・プライバシーの内を埋める:
- tokushoho.html: 販売事業者／運営責任者／所在地／電話番号／メールアドレス／送料／返品条件
- privacy.html: 屋号／メールアドレス／利用する運送会社／保管期間／制定日

## ローカルで見る方法
- フロントだけ: このフォルダで `python3 -m http.server 8000` → http://localhost:8000
- 決済サーバー: `npm install` のあと `.env` に STRIPE_SECRET_KEY を入れて `node server.js`（ポート4242）
