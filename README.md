# Laboratorium 13/13D PAwChO

Robert Horbaczewski

Zbudowano prosty plik docker-compose.yml pozwalający na uruchomienie stacka LEMP wraz z phpMyAdmin. Konfiguracja danych wrażliwych jako secrets.

Uruchomienie stosu LEMP:
```bash
(base) roberthorbaczewski@MacBook-Air-M2-Robert Lab13 % docker compose up -d
[+] up 7/7
 ✔ Network lab13_backend   Created                                                                                                               0.0s
 ✔ Network lab13_frontend  Created                                                                                                               0.0s
 ✔ Volume lab13_mysql_data Created                                                                                                               0.0s
 ✔ Container php           Created                                                                                                               0.1s
 ✔ Container mysql         Created                                                                                                               0.1s
 ✔ Container phpmyadmin    Created                                                                                                               0.2s
 ✔ Container nginx         Created                                                                                                               0.2s
```

Potwierdzenie uruchomienia wszystkich wymaganych mikrousług:
```bash
(base) roberthorbaczewski@MacBook-Air-M2-Robert Lab13 % docker compose ps
NAME         IMAGE              COMMAND                  SERVICE      CREATED          STATUS          PORTS
mysql        mysql:8.4          "docker-entrypoint.s…"   mysql        24 seconds ago   Up 23 seconds   3306/tcp, 33060/tcp
nginx        nginx:1.26         "/docker-entrypoint.…"   nginx        24 seconds ago   Up 23 seconds   0.0.0.0:4001->80/tcp, [::]:4001->80/tcp
php          php:8.3-fpm        "docker-php-entrypoi…"   php          24 seconds ago   Up 23 seconds   9000/tcp
phpmyadmin   phpmyadmin:5.2.2   "/docker-entrypoint.…"   phpmyadmin   24 seconds ago   Up 23 seconds   0.0.0.0:6001->80/tcp, [::]:6001->80/tcp
```

Potwierdzenie utworzenia sieci frontend i backend:
```bash
(base) roberthorbaczewski@MacBook-Air-M2-Robert Lab13 % docker network ls
NETWORK ID     NAME                      DRIVER    SCOPE
57ce58c0b630   lab13_backend             bridge    local
8a6b4439b9e6   lab13_frontend            bridge    local
```

Strona PHP wyświetlana przez serwer nginx na porcie 4001:
![Strona PHP](screenshots/zrzut1)

Logowanie do phpMyAdmin:
![phpMyAdmin](screenshots/zrzut2)

Utworzenie testowej bazy danych:
![Baza danych](screenshots/zrzut3)
