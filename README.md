# solving curl error 28 with composer
This page about How To Fix the “cURL Error 28: Connection Timed Out” with Curl and composer v2 .


## this page will be continuse update .

### Note:
This solution is temporary until the problem is resolved by composer team

## Problem Statment
composer v1 was use many of servers for packages mirroring .

but composer v2 do not use mirroring .

so , for some reasons the composer 2 package servers get timeout in some countries .

## remove composer v2, and make sure it is removed completly .
make sure it is removed by running
```
composer --version
```
you must see  composer command not found.


## install composer version 1.10.23 (latest 1.x version) .

### linux and macOS
```
php -r "copy('https://getcomposer.org/download/1.10.23/composer.phar', 'composer.phar');"
chmod +x composer.phar
sudo mv composer.phar /usr/local/bin/composer
composer --version  // just to Verify that Composer is installed with needed version 1.10.23
```

### Window OS

```
Download the Composer installer from the official website: https://getcomposer.org/download/1.10.23/composer_windows_x86_64.exe

Double-click the downloaded file to run the installer.

Follow the on-screen instructions to complete the installation process.

After installation, open a Command Prompt or PowerShell window and run the following command to verify that Composer is installed:
composer --version

```

change composer config to use neasest package mirror with your country , for Ex in yemen use China Packagist mirror

### First Way

you can change this config global for all composer packages in all projects with this command
```
composer config -g repo.packagist composer https://packagist.phpcomposer.com
```

### Second Way

change it for current project:
open composer.json file in current project and add these lines to it
```
"repositories": {
    "packagist": {
        "type": "composer",
        "url": "https://packagist.phpcomposer.com"
    }
}
```

and make composer update .
it will show you (composer v1 is deprcated) .. no problem .

## Additional Info:
some another mirrors

```
Location | Mirror | Github | Sync
------- | -------- | -------- | --------
Asia | packagist.kr | packagistkr/packagist-mirror
Asia | packagist.co.za | webysther/packagist-mirror
Asia | mirrors.aliyun.com/composer | webysther/packagist-mirror
Asia | packagist.in | webysther/packagist-mirror
Europe | packagist.eu | webysther/packagist-mirror
Europe | packagist.fr | webysther/packagist-mirror
Europe | packagist.de | webysther/packagist-mirror
North America | packagist.io | webysther/packagist-mirror
North America | packagist.us | webysther/packagist-mirror
South America | packagist.br | webysther/packagist-mirror

```
