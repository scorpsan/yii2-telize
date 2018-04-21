# yii2-geoip

An extension that allows you to obtain the visitor's IP address and location information from any IP address. Uses http://sypexgeo.net/ for online and http://www.ip2location.com/ library for offline data retrieval.

## Installation

The preferred way to install this extension through [composer](http://getcomposer.org/download/).

You can set the console

```
$ composer require "scorpsan/yii2-geoip"
```

or add

```
"scorpsan/yii2-geoip": "*"
```

in ```require``` section in `composer.json` file.

## Using

Once the extension is installed, simply use it in your code by  :

Add following code to your configuration file of application:

```php
...
'components' => [
    ...
    'geoIp' => [
        'class' => 'scorpsan\geoip\GeoIp',
        'externalIp' => YII_ENV_DEV,
    ],
    ...
],
...
```

Get information from Ip User:
Online

```php
var_dump(Yii::$app->geoIp->info);
```

Offline

```php
var_dump(Yii::$app->geoIp->infoDb);
```

Get information from Select Ip:
Online

```php
var_dump(Yii::$app->geoIp->getInfo('255.255.255.255'));
```

Offline
```php
var_dump(Yii::$app->geoIp->getInfoDb('255.255.255.255'));
```

Get User Ip:

```php
var_dump(Yii::$app->geoIp->ip);
```

## Return Data

```php
Online
     * Returned information by IP address with following paramters:
     * - `ip`               - Visitor IP address, or IP address specified as parameter.
     * - `city`             - Object Region information
     * -- [id] => 625144
     * -- [lat] => 53.9
     * -- [lon] => 27.56667
     * -- [name_ru] => Минск
     * -- [name_en] => Minsk
     * -- [name_de] => Minsk
     * -- [name_fr] => Minsk
     * -- [name_it] => Minsk
     * -- [name_es] => Minsk
     * -- [name_pt] => Minsk
     * -- [okato] => 5000000000
     * -- [vk] => 282
     * -- [population] => 1742124
     * - `region`           - Object Region information
     * -- [id] => 625143
     * -- [lat] => 53.9
     * -- [lon] => 27.57
     * -- [name_ru] => Минск
     * -- [name_en] => Horad Minsk
     * -- [name_de] => Minsk
     * -- [name_fr] => Minsk
     * -- [name_it] => Minsk
     * -- [name_es] => Minsk
     * -- [name_pt] => Minsk
     * -- [iso] => BY-HM
     * -- [timezone] => Europe/Minsk
     * -- [okato] => 5
     * -- [auto] => 7
     * -- [vk] => 0
     * -- [utc] => 3
     * - `country`          - Object Country information
     * -- [id] => 36
     * -- [iso] => BY
     * -- [continent] => EU
     * -- [lat] => 53
     * -- [lon] => 28
     * -- [name_ru] => Беларусь
     * -- [name_en] => Belarus
     * -- [name_de] => Weißrussland
     * -- [name_fr] => Biélorussie
     * -- [name_it] => Bielorussia
     * -- [name_es] => Bielorrusia
     * -- [name_pt] => Bielorrússia
     * -- [timezone] => Europe/Minsk
     * -- [area] => 207600
     * -- [population] => 9685000
     * -- [capital_id] => 625144
     * -- [capital_ru] => Минск
     * -- [capital_en] => Minsk
     * -- [cur_code] => BYR
     * -- [phone] => 375
     * -- [neighbours] => PL,LT,UA,RU,LV
     * -- [vk] => 3
     * -- [utc] => 3
     * - `error`            - Error data.
     * - `request`          - Request code.
     * - `created`          - Date create info in dstsbase.
     * - `timestamp`        - Timestanp request.
     *
     * @return array|false
     */
```

```php
Offline
     * Returned information by IP address with following paramters:
     * - `ipAddress`       - Visitor IP address, or IP address specified as parameter.
     * - `countryName`     - Name Country in English.
     * - `countryCode`     - Two-letter ISO 3166-1 alpha-2 country code.
     *
     * @return array|false
     */
```

## License

yii2-geoip is released under the BSD 3-Clause License.
