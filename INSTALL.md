## About Muscle Lab

## 設定 laradock

1. 設定 laradock
```bash
cd laradock
cp .env.example .env 
```

2.1 編輯 laradock .env
```php
# 時區
WORKSPACE_TIMEZONE=UTC => WORKSPACE_TIMEZONE=Asia/Taipei

WORKSPACE_INSTALL_PG_CLIENT=true

PHP_FPM_INSTALL_PG_CLIENT=true
PHP_FPM_INSTALL_PGSQL=true

PHP_WORKER_INSTALL_PGSQL=true
```

2.2 編輯 docker-compose.yml
```
### PostgreSQL ###########################################
    postgres:
        environment:
            - PGDATA=/tmp
```

3. 使用 Nginx PostgreSQL PgAdmin
```bash
docker-compose up -d nginx postgres pgadmin workspace
```

## 設定 laravel
1. 進入 docker 環境
```bash
docker-compose exec workspace bash

# or (windows)
winpty docker-compose exec workspace bash

# 成功會顯示
root@xxxxxxxx:/var/www
```

2. 安裝 laravel
```bash
cp .env.example .env

composer install

php artisan key:gen
```

3. 編輯 .env
```
DB_HOST=127.0.0.1 => DB_HOST=postgres
```


```
php artisan migrate --seed

npm install

npm run dev
```
