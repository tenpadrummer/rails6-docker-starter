# Rails 7 + Docker + PostgreSQLでのローカル環境構築スターター

# バージョン

```
Ruby: 3.1
Ruby on Rails: 7.0.2
PostgreSQL: 13.2
```

# はじめ方

```
docker-compose run --no-deps web rails new . --force --database=postgresql
```

database.ymlを編集
```
default: &default
  adapter: postgresql
  encoding: unicode
  host: postgres
  username: root
  password: root
  pool: 5

development:
  <<: *default
  database: app_development

test:
  <<: *default
  database: app_test

production:
  <<: *default
  database: app_production
  password: <%= ENV['APP_DATABASE_PASSWORD'] %>
```
