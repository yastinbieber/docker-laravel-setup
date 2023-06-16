# docker-laravel-setup
docker環境でLaravelインストールセットアップ

## ローカル環境構築
.env.exampleをコピーして.envを作成。
```bash
cp laravel/.env.example laravel/.env
```

### イメージをビルドしてコンテナを起動。
```bash
docker-compose build
docker-compose up -d
```

### Laravelアプリケーションセットアップ
コンテナに入って権限変更、composer install, アプリケーションキー生成、シンボリックリンク、migrateを実行して完了。
```bash
docker-compose exec app bash
cd laravel
chmod -R 777 storage bootstrap/cache
composer install
php artisan key:generate
php artisan storage:link
php artisan migrate
exit
```
