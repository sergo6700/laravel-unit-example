## Installation

### Docker
- Copy file `.env.docker.example` to `.env`
- Run `docker-compose up -d` command
- Enter the `laravel_test_examples_workspace` container
```
docker exec -ti laravel_test_examples_workspace /bin/bash
```
- Install project dependencies
```
composer install
yarn
```
- Run migration
```
php artisan migrate
php artisan migrate --database=mysql_test
```
- Generate application encryption key
```
php artisan key:generate
```
- Check the service online at http://0.0.0.0:8000/

## Integrate with CI services
- For [Scrutinizer CI](http://scrutinizer-ci.com/) integration, please refer [.scrutinizer.yml](./.scrutinizer.yml) configuration file.
- For [Travis CI](https://travis-ci.org) integration, please refer [.travis.yml](./.travis.yml). Moreover, Travis CI only support Mysql 5.6 by default, that causes the migration to be [failed](https://github.com/laravel/framework/issues/17508). Therefore, the [.travis.install-mysql-5.7.sh](./.travis.install-mysql-5.7.sh) file is also included too, to replace the default 5.6 version with the newest 5.7 version.
- For [Circle CI](https://circleci.com/), please refer [.circleci/config.yml](./.circleci/config.yml) file.
- For [Framgia CI](https://github.com/framgia/ci-service-document), please refer [.drone.yml](./.drone.yml) and [.framgia-ci.yml](./.framgia-ci.yml) files.
