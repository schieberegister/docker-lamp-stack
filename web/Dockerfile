FROM alpine:latest


LABEL maintainer="hb@beohof.de"

RUN adduser -D -g 'www' www

RUN apk add --no-cache nginx supervisor php7-fpm php7-mcrypt php7-soap \
php7-openssl php7-gmp php7-pdo_odbc php7-json php7-dom \
php7-pdo php7-zip php7-mysqli php7-sqlite3 php7-apcu   \
php7-pdo_pgsql php7-bcmath php7-gd php7-odbc \
php7-pdo_mysql php7-pdo_sqlite php7-gettext \
php7-xmlreader php7-xmlrpc php7-bz2 php7-iconv \
php7-pdo_dblib php7-curl php7-ctype

RUN mkdir /www && \
chown -R www:www /var/lib/nginx && \
chown -R www:www /www


COPY config/nginx.conf /etc/nginx/nginx.conf
COPY config/supervisord.conf /etc/supervisord.conf
COPY config/php-fpm.conf /etc/php7/php-fpm.conf
COPY config/php.ini /etc/php7/php.ini

ENTRYPOINT ["supervisord"]
EXPOSE 80
