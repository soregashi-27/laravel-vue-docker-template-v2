DockerをベースとしたLaravel, MySQL, nginxの開発環境。

# 環境構築手順
## git clone

### cloneしたDirectoryに移動

## Laravelをインストール
```
composer install
```

### php-cs-fixerのライブラリ情報をインストール
```
```

### `.env`ファイルの設定


### アプリケーションキーをつくる
```
```

### シンボリックリンクをつくる
```
```

### 書き込み権限を追加する
```
```

## Dockerで立ち上げる

### Docker composeでBuildする
```
docker compose up -d --build
```

立ち上がっているか確認
```
docker ps -a
```

### バージョンの確認
・Laravel
```
php artisan -V
```

・php-cs-fixer
```

```

・MySQL
```
```

・nginx
```
```

・npm
```
npm -V
```

・Node.js
```
node -V
```

### Web Browser上で画面を確認する
・Laravel
```
http://127.0.0.1/
```

・PhpMyAdmin
```
http://127.0.0.1:8080/
```

## データベースの設定
### `.env`ファイルの設定を確認する
`.env.example`ファイルを書き換えてコピーする

### Migrateする
```
php artisan migrate
```

### PhpMyAdminでMigrateしたデータベースとテーブルが作成されているかを確認
```
http://127.0.0.1:8080/
```

## ログの設定
### Laravelのログをコンテナログに表示させる
`backend/.env` を修正する
```
LOG_CHANNEL=stderr
```

### 表示されるかを確認

`backend/routes/web.php`に追記
```
Route::get('/', function () {
    logger('welcome route.');
    return view('welcome');
});
```

**logをみる方法3パターン**

```
$ docker compose logs

# -f でログウォッチ
$ docker compose logs -f

# サービス名を指定してログを表示
$ docker compose logs -f app
```

`docker compose logs -f app`のあとに、`http://127.0.0.1:8080/`に接続するlog上にこんな感じで表示される
```
app_1  | [2021-07-25 05:48:53] local.DEBUG: welcome route.  
app_1  | 172.20.0.3 -  25/Jul/2021:05:48:51 +0000 "GET /index.php" 200
```





