FROM php:8.0.10-fpm

RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev libpq-dev zip \
    && docker-php-ext-install intl opcache pdo pdo_pgsql pgsql \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

WORKDIR /var/www/symfony_docker

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony
RUN git config --global user.email "sajeev.nair174@gmail.com" \
    && git config --global user.name "Sajeev Nair"

RUN  sh -c "$(curl -fsSL https://starship.rs/install.sh)" -- --yes >> /dev/null
RUN echo 'eval "$(starship init bash)"' >> ~/.bashrc