# webpro_06

## 第7回 やってみよう

### (1)(2) じゃんけんをラジオボタンで実装
- `public/janken2.html`：最初の入力フォーム（ラジオボタンでグー・チョキ・パーを選ぶ）
- `views/janken2.ejs`：勝敗の表示と次の入力フォーム
- `app5.js`：`/janken2` を追加（元の `/janken` は変更していない）
- 確認方法：`node app5.js` を実行し，http://localhost:8080/public/janken2.html を開く

### (3) input要素の type，name，id の働き
- **type**：入力欄の種類を指定する．例えば text なら文字入力，radio ならラジオボタン，number なら数字のみ，submit なら送信ボタンになる．
- **name**：フォームを送信したときのパラメータ名になる．サーバ側では `req.query.name の値` で入力内容を受け取る．ラジオボタンは同じ name を付けることで1つのグループになり，その中から1つだけ選べるようになる．
- **id**：ページ内でその要素を区別するための名前である．`<label for="id名">` と組み合わせることで，ラベルと入力欄が対応し，ラベルをクリックしても選択できるようになる．

### (4) htmlファイルとejsファイルの使い分け
htmlファイルは，最初の入力フォームのように内容が変わらない静的なページに使い，public フォルダに置く．
ejsファイルは，じゃんけんの結果や勝ち数のように，サーバのプログラムの処理結果によって内容が変わる動的なページに使い，views フォルダに置く．サーバ側で `res.render()` を使い，値を埋め込んでからブラウザに返す．

## 第9回 一覧表示と詳細表示

### やってみよう(2) レポート用システムの設計
- `design.md`：開発する3つのシステム（アニメ一覧，ゲームの記録，筋トレメニュー）の対象，ページ遷移，スキーマ

### 授業の例
- `app5.js`：`station2`（項目：id, code, name, change, passengers, distance）と `/keiyo2`（一覧），`/keiyo2/:number`（詳細）を追加
- `views/keiyo2.ejs`：一覧表示（駅名から詳細ページへリンク）
- `views/keiyo2_detail.ejs`：詳細表示
- 確認方法：`node app5.js` を実行し，http://localhost:8080/keiyo2 を開く

### やってみよう(3) station2へのデータ追加
- `public/keiyo2_add.html`：入力フォーム（駅コード，駅名，乗り換え線，乗降客数，東京駅からの距離）
- `app5.js`：`/keiyo2_add` を追加．IDは自動で振り，乗降客数と距離は `Number()` で数値に変換してから追加する．登録後は一覧（/keiyo2）に戻る
- 確認方法：http://localhost:8080/public/keiyo2_add.html から登録する
