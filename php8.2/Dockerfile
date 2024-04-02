FROM php:8.2.0-fpm

#RUN apt-get update && apt-get install -y \
#        libfreetype6-dev \
#        libjpeg62-turbo-dev \
#        libpng-dev \
#    && docker-php-ext-configure gd --with-freetype --with-jpeg \
#    && docker-php-ext-install -j$(nproc) gd
#
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli


# Install any custom system requirements here
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
  curl \
  libicu-dev \
  libmemcached-dev \
  libz-dev \
  libpq-dev \
  libjpeg-dev \
  libpng-dev \
  libfreetype6-dev \
  libssl-dev \
  libxml2-dev \
  libbz2-dev \
  libzip-dev \
  libonig-dev \
  libjpeg62-turbo-dev \
  && rm -rf /var/lib/apt/lists/*


# Install various PHP extensions
RUN docker-php-ext-configure bcmath --enable-bcmath \
  && docker-php-ext-configure pcntl --enable-pcntl \
  && docker-php-ext-configure pdo_mysql --with-pdo-mysql \
  && docker-php-ext-configure mbstring --enable-mbstring \
  && docker-php-ext-configure soap --enable-soap \
  && docker-php-ext-install \
  bcmath \
  intl \
  mbstring \
  mysqli \
  pcntl \
  pdo_mysql \
  soap \
  sockets \
  zip \
  && docker-php-ext-configure gd \
  --enable-gd \
  --with-jpeg \
  --with-freetype && \
  docker-php-ext-install gd \
  && docker-php-ext-install opcache \
  && docker-php-ext-enable opcache

# Install redis extension
# RUN pecl install redis && docker-php-ext-enable redis

# Copy opcache configration
# COPY ./php/opcache.ini /usr/local/etc/php/conf.d/opcache.ini

# # Install xDebug, if enabled
# ARG INSTALL_XDEBUG=false
# RUN if [ ${INSTALL_XDEBUG} = true ]; then \
#     # Install the xdebug extension
#     pecl install xdebug && \
#     docker-php-ext-enable xdebug \
# ;fi

# Copy xdebug configration for remote debugging
# COPY ./xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

# Copy timezone configration
# COPY ./php/timezone.ini /usr/local/etc/php/conf.d/timezone.ini

# Add default configuration files
# ADD configs/php.ini /usr/local/etc/php/
# ADD configs/php-fpm.d/www.conf /usr/local/etc/php-fpm.d/
#/etc/php/7.2/fpm/pool.d
#/usr/local/etc/php-fpm.d/www.conf 

# # Set timezone
# RUN rm /etc/localtime
# RUN ln -s /usr/share/zoneinfo/Asia/Ho_Chi_Minh /etc/localtime
# RUN "date"


