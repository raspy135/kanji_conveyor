# 漢字コンベア

GENKI I の漢字よみ小テストを、ベルトコンベア式のスマホ向けWebゲームにしたもの。
ながれてくる単語のイラストと漢字を見て、4つのよみから正解をタップします。

## あそびかた

- `index.html` をブラウザで開くだけ（スマホ・PCどちらでもOK）。
  画像を読み込むため、このリポジトリの中身をまるごと置いてください。

## Cloudflare Pages で公開

`main` にプッシュすると GitHub Actions（`.github/workflows/deploy.yml`）が
Cloudflare Pages の直接アップロード型プロジェクトへ自動でデプロイします。

初回だけ設定が必要です。

1. Cloudflare → マイプロフィール → API トークン → トークンを作成
   （テンプレート「カスタムトークン」、権限: アカウント / Cloudflare Pages / 編集）
2. GitHub のこのリポジトリ → Settings → Secrets and variables → Actions に登録
   - `CLOUDFLARE_API_TOKEN`: 1 のトークン
   - `CLOUDFLARE_ACCOUNT_ID`: Cloudflare ダッシュボードの URL や Workers & Pages 画面右側に出るアカウント ID
3. `deploy.yml` の `PAGES_PROJECT` を Pages のプロジェクト名に合わせる

手動で流したいときは GitHub の Actions タブ → Deploy to Cloudflare Pages → Run workflow。

## 問題の追加

`questions.js` を開いて1行足すだけ。

```js
["水", "みず", "すい", "みつ", "もず"],   // 漢字, 正解, ハズレ×3（ハズレは省略可）
```

セット（レッスン）を増やすと、タイトル画面にボタンが出ます。
意味の絵文字と英語は `WORD_ICONS` に1行足すと出ます（なくてもOK）。

## イラスト

`img/漢字.png` を置くと自動でそのイラストが出ます（例: `img/水.png`）。
最初から入っている絵は [Microsoft Fluent Emoji](https://github.com/microsoft/fluentui-emoji)（MITライセンス、`img/LICENSE-fluentui-emoji.txt`）です。
いらすとやの絵に替えたいときは、同じファイル名で上書きしてください。
