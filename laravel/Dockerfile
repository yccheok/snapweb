FROM php:7.2.8-fpm-alpine3.7

COPY . /var/www

WORKDIR /var/www/html

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN composer install

RUN apk update && \
    apk add postgresql-dev && \
	apk add nodejs && \
    apk add autoconf gcc make libpng-dev

RUN docker-php-ext-install pdo_pgsql

RUN npm install

CMD ["php-fpm", "-F"]