# サイト構成設計（草案）

> ステータス: draft — 確定したら docs/ に promote する

---

## 全体構成

```
RunStay/
├── index.html          ← トップ（LP + 検索）         ★現在ここだけある
├── race/
│   └── [id].html       ← 大会詳細ページ
├── area/
│   └── [region].html   ← エリア別一覧ページ
├── data/
│   └── marathons.json  ← 大会データ（CSVから変換）
└── assets/
    ├── style.css
    └── app.js
```

---

## 各ページの役割

### / トップページ（index.html）
- LP（ヒーロー・機能紹介・CTA）
- 検索UI（地域・時期・種別）
- 検索結果 → 地図表示
- 大会カードクリック → 詳細ページへ遷移 or モーダル表示

### /race/[id] 大会詳細ページ
- 大会基本情報（名前・日程・距離・定員・参加費）
- エントリーリンク
- 会場周辺地図（ホテル・駅・コンビニ）
- 近くのおすすめホテル一覧（楽天トラベルAPI連携予定）

### /area/[region] エリア別一覧
- 「関東の大会一覧」など地域でまとめたページ
- SEO目的（「東京 マラソン 大会」などで検索流入）

---

## データの流れ

```
marathons.csv（手動入力）
    ↓ 変換スクリプト（or 手動）
marathons.json
    ↓ fetch
index.html / 各ページ
```

---

## 開発フェーズ

### Phase 1（今すぐ）
- [x] 検索UI・地図表示（完成済み）
- [ ] marathons.csv に100件入力
- [ ] CSV → JSONに変換してindex.htmlに組み込む

### Phase 2
- [ ] 大会詳細ページ（race/[id].html）
- [ ] 楽天トラベルAPI連携（ホテル空室・料金）
- [ ] エリア別一覧ページ

### Phase 3
- [ ] スマホアプリ版（React Native or PWA）
- [ ] ユーザーアカウント・お気に入り機能
- [ ] 大会カレンダー表示

---

## 技術スタック（現状・予定）

| 役割 | 技術 | 状態 |
|------|------|------|
| フロントエンド | HTML / CSS / Vanilla JS | ✅ 稼働中 |
| 地図 | Leaflet.js + OpenStreetMap | ✅ 稼働中 |
| 周辺施設 | Overpass API | ✅ 稼働中 |
| 大会データ | JSONファイル（静的） | 🔲 Phase1 |
| ホテル空室 | 楽天トラベルAPI | 🔲 Phase2 |
| ホスティング | GitHub Pages | ✅ 稼働中 |

---

*作成: 2026-06-03 / 要レビュー*
