# plesk.domains.raspbian
Environment to deploy and manage the parkingomat.plesk module on RPI ZERO W

+ [index.php](http://raspberrypi:8080/index.php)
+ 
# parkingomat/plesk.domains.php
Plesk api client to get all domains

[parkingomat/plesk.domains.php: PLesk api client to get all domains](https://github.com/parkingomat/plesk.domains.php)

---

# api
API with OpenApi (Swagger)  documentation based on Nodejs

## Functions
+ user auth
+ obsluga API github
+ komunikacja z github
+ komunikacja z PLESK
+ deploy from github to plesk


Statystyki:

Lista ostatnio wygenerowanych paczek

Lista plikow uzywanchy i wersji



podpowiedzi

Gdzie mozna dodac nowa wersje

Testowanie jakosci kodu

Mozliwosc za pomoca jednego klineiecia

Lub podania pliku

Oda razu og edytowac

## cron

To run a cron job at every system boot, add a string called @reboot to the end of the task list. The job defined by this string runs at startup, immediately after Linux reboots.

Use the following syntax when adding a @reboot string:

    @reboot [path to command] [argument1] [argument2] … [argument n]
    @reboot [part to shell script]

For example, if we wanted to have the system date written in a file called date.txt when Linux restarts, we would add the following string:

    crontab -e

    @reboot date >> ~/date.txt
    @reboot sh ~/plesk.domains.raspbian/.apiexec/start
    @reboot nohup php -S 0.0.0.0:8080 -t ~/plesk.domains.raspbian/php

    sudo reboot

cat ~/plesk.domains.raspbian/.apiexec/start
## TODO

+ support by PROMAGEN

one file to start promagen project


## API foundation

.promagen - web management dla devops
.apicra - skrypty do instalacji env
.apifunc - funkcje, implementacja apiunit
.apiunit - metadane potrzebne do stworzenia aplikacji
.apibuild - budowanie plaikacji, deployment






## packagist
[parkingomat/plesk.domains.php - Packagist](https://packagist.org/packages/parkingomat/plesk.domains.php)
https://packagist.org/packages/parkingomat/plesk.domains.php


## composer package name

    "parkingomat/plesk.domains.php"



TODO:

.apiterminal

## package install


## Install on raspbian

Raspbian config

https://www.tomshardware.com/reviews/raspberry-pi-headless-setup-how-to,6028.html

Clean

    sudo apt autoremove -y

Update

    sudo apt update -y

Upgrade

    sudo apt upgrade --yes

GIT INSTALL

    sudo apt install -y git


# First Steps on linux

## GIT CLONE
git clone https://github.com/parkingomat/plesk.domains.raspbian.git && cd plesk.domains.raspbian
    
    sh .apifork/download


### install packages for composer
    sh .apitee/install

### install packages for composer
    sh .apibuild/install

### install functions for apifunc
    sh .apifunc/install

### start
    sh .apiexec/start

    nohup php -S 0.0.0.0:8080 -t php

### open in browser
    sh .apicra/browser

http://raspberrypi:8080/index.php
http://raspberrypi:8080/index.php?hostname=softreck.com
### Install PHP 7 and common modules
Install PHP
```
sudo apt install -y php
php -v
```

## Install modules
If you need some other version in case your code requires 7.2 or 7.4, just adjust the version in the package names and commands. Later we will show how you can have multiple PHP version running in parallel.

### PHP 7.3
```
sudo apt install -y php7.3-cli php7.3-fpm php7.3-opcache php7.3-curl php7.3-mbstring php7.3-pgsql php7.3-zip php7.3-xml php7.3-gd
```
### PHP 7.4
```
sudo apt install -y php7.4-cli php7.4-fpm php7.4-opcache php7.4-curl php7.4-mbstring php7.4-pgsql php7.4-zip php7.4-xml php7.4-gd
```

Update composer dependencies

```
php composer.phar install

sh .apicra/install

sudo php -S 0.0.0.0:8080 -t src

sh .apicra/start
```

raspberrypi:8080

raspberrypi:8080/domains.php

Config

    sudo nano /etc/php/7.3/cli/php.ini


NOTICE: To enable PHP 7.3 FPM in Apache2 do:
NOTICE: a2enmod proxy_fcgi setenvif
NOTICE: a2enconf php7.3-fpm

### Add the PHP repository

So how to get a fresh version of PHP then ? Luckily the Debian PHP maintainer hosts a repository with fresh version of PHP and it includes armhf (armv7 only!) versions too. Lets start by adding the repository PGP key:
```
wget -q https://packages.sury.org/php/apt.gpg -O- | sudo apt-key add -
```
And add the PHP repository to your apt sources
```
echo "deb https://packages.sury.org/php/ buster main" | sudo tee /etc/apt/sources.list.d/php7.list
```
Update repository pacakge index
```
sudo apt update
```
In case apt complains about "The method driver /usr/lib/apt/methods/https could not be found", install the following optional packages:
```
sudo apt install ca-certificates apt-transport-https
```

Install Apache and FastCGI module

Next we will install Apache and the required extra module for FastCGI support:

```
sudo apt install apache2 libapache2-mod-fcgid
```

## Apache 2

Enable fpm proxy moudle and php-fpm configuration

```
sudo a2enmod proxy_fcgi
sudo a2enconf php7.3-fpm
```

And reload Apache

```
sudo systemctl reload apache2
```

## install on windows

with local composer.phar file

    php composer.phar require parkingomat/plesk.domains.php

global installed composer in system

    composer require parkingomat/plesk.domains.php


## composer install

    php composer.phar install



## raspberry and PHP

This tutorial will show installation instructions for **PHP 7.3** but in case you need to use something else like 7.4, just adjust the versions in the package and commands. And there is also the issues of the recommended way to run PHP these days. It is **not** as a Apache module,libapache2-mod-php, anymore!

What we need to do is:

1.  Add apt source repository for uptodate PHP packages
2.  Install Apache with required modules
3.  Install PHP 7 with optional extras. In this guide we will start with installation of version 7.3
4.  Optiona: Parallel install other versions

## Add the PHP repository

So how to get a fresh version of PHP then ? Luckily the [Debian PHP maintainer](https://deb.sury.org/) hosts a repository with fresh version of PHP and it includes armhf (armv7 only!) versions too. Lets start by adding the repository PGP key:

    wget -q https://packages.sury.org/php/apt.gpg -O- | sudo apt-key add -

And add the PHP repository to your apt sources

    echo "deb https://packages.sury.org/php/ buster main" | sudo tee /etc/apt/sources.list.d/php7.list

Update repository pacakge index

    sudo apt update

In case apt complains about "_The method driver /usr/lib/apt/methods/https could not be found_", install the following optional packages:

    sudo apt install ca-certificates apt-transport-https

## Install Apache and FastCGI module

Next we will install Apache and the required extra module for FastCGI support:

    sudo apt install apache2 libapache2-mod-fcgid

Verify that apache work by going to [http://YOUR-RPI-IP](http://YOUR-RPI-IP) with your browser. If all is well and you get a response, continue with installation of PHP.

## Install PHP 7 and common modules

Next we will install **PHP 7.3** with some common modules, but **not** the Apache module version! Instead we will use [**php-fpm**, the FastCGI](https://wiki.apache.org/httpd/PHP-FPM) version.


## Install modules
If you need some other version in case your code requires 7.2 or 7.4, just adjust the version in the package names and commands. Later we will show how you can have multiple PHP version running in parallel.

### PHP 7.3
```
sudo apt install -y php7.3-cli php7.3-fpm php7.3-opcache php7.3-curl php7.3-mbstring php7.3-pgsql php7.3-zip php7.3-xml php7.3-gd
```
### PHP 7.4
```
sudo apt install -y php7.4-cli php7.4-fpm php7.4-opcache php7.4-curl php7.4-mbstring php7.4-pgsql php7.4-zip php7.4-xml php7.4-gd
```

Enable fpm proxy moudle and php-fpm configuration

     sudo a2enmod proxy\_fcgi
     sudo a2enconf php7.3-fpm

And reload Apache

 sudo systemctl reload apache2


## Test the installation

### Test cli PHP

php7.3 -v

It should response with something close to

PHP 7.3.27-9+0~20210227.82+debian10~1.gbpa4a3d6 (cli) (built: Feb 27 2021 15:50:50) ( NTS )

Copyright (c) 1997-2018 The PHP Group

Zend Engine v3.3.27, Copyright (c) 1998-2018 Zend Technologies

 with Zend OPcache v7.3.27-9+0~20210227.82+debian10~1.gbpa4a3d6, Copyright (c) 1999-2018, by Zend Technologies

### Test serving a PHP page

Create a "_test.php_" file in _/var/www/html_ with your favorite editor, use the contents:

    <?php [phpinfo](http://fi2.php.net/manual/en/function.phpinfo.php)(); ?>

And the point your browser to _[http://YOUR-RPI-IP/test.php](http://YOUR-RPI-IP/test.php)_

Your browser should now show the PHP information page with all kinds of details.


## Publishing a new version

Note that you need 2FA enabled on NPM, publishing with Yarn gives error, use NPM directly for this:

```bash
npm version patch|minor|major
```

## Contributing

We welcome code changes that improve this library or fix a problem, please make sure to follow all best practices and add tests if applicable before submitting a Pull Request on Github. We are very happy to merge your code in the official repository. Make sure to sign our [Contributor License Agreement (CLA)](https://docs.google.com/forms/d/e/1FAIpQLScFKsKkAJI7mhCr7K9rEIOpqIDThrWxuvxnwUq2XkHyG154vQ/viewform) first. See our license file for more details.

## We are hiring

We've recently closed a [$38 million Series B funding round](https://techcrunch.com/2021/03/04/stream-raises-38m-as-its-chat-and-activity-feed-apis-power-communications-for-1b-users/) and we keep actively growing.
Our APIs are used by more than a billion end-users, and you'll have a chance to make a huge impact on the product within a team of the strongest engineers all over the world.

Check out our current openings and apply via [Stream's website](https://softreck.dev/team/#jobs).

---
+ [edit](https://github.com/parkingomat/plesk.domains.php/edit/main/README.md)
+ [git](https://github.com/parkingomat/plesk.domains.php)
```
https://github.com/parkingomat/plesk.domains.php.git
```