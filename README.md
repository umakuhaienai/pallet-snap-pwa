# Palette Snap PWA

スマホ・PC共通で使える、限定カラーパレット向け近似色検索ツールです。

## ファイル構成

- `index.html` — 本体
- `manifest.webmanifest` — PWA設定
- `service-worker.js` — オフラインキャッシュ
- `icons/` — アプリアイコン

## まずPCで試す

PWAのService Workerは `file://` 直開きでは動きません。
このフォルダでローカルサーバーを起動してください。

### Pythonがある場合

```bash
python -m http.server 8000
```

その後ブラウザで:

```text
http://localhost:8000
```

を開きます。

## GitHub Pagesで公開する

1. GitHubで新しいリポジトリを作成（例: `palette-snap`）
2. このZIPの中身をリポジトリ直下へアップロード
3. GitHubの `Settings` → `Pages`
4. `Build and deployment` の Source を `Deploy from a branch`
5. Branch を `main` / `(root)` にして Save
6. 数分後に表示されたURLを開く

GitHub PagesはHTTPSなのでPWAとしてインストールできます。

## Android

Chromeで公開URLを開き、
メニュー → 「ホーム画面に追加」または「アプリをインストール」。

## Windows / PC

Chrome / Edgeで公開URLを開くと、
アドレスバー付近のインストールボタンまたはブラウザメニューからインストールできます。

## 主な機能

- HEX入力
- カラーピッカー
- 画像からタップ採色
- Lab色空間（ΔE76）で近似色検索
- 上位5色表示
- HEXコピー
- 複数パレット保存
- パレット名変更
- localStorageによる端末保存
- オフライン起動

## 更新時の注意

`service-worker.js` 内の

```js
const CACHE = 'palette-snap-v1';
```

を `palette-snap-v2` のように変更すると、新しいファイルへキャッシュ更新しやすくなります。
