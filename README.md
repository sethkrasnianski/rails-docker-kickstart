# Rails Docker Kickstarter

## Setup

Generate the Rails application and build the respective docker containers.

```sh
docker-compose run web rails new . --force --no-deps --database=postgresql
docker-compose build
```

Configure database connection by replacing the contents of `config/database.yml` with the following:

```yml
default: &default
  adapter: postgresql
  encoding: unicode
  host: db
  username: postgres
  password:
  pool: 5

development:
  <<: *default
  database: myapp_development


test:
  <<: *default
  database: myapp_test
```

Now you're ready to boot the app!

```
docker-compose up
```

Finally, let's create the database.

```
docker-compose run web rake db:create
```
