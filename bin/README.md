This folder contains scripts for performing various tasks related to the MARTI dice server.

## Create and initialize the staging database

1. Login to `dice.tripleawarclub.org`.
1. Change to the directory where you have cloned the `triplea-game/dice-server` repo.
1. Create the staging database:
    ```bash
    $ ./bin/create_staging_db
    ```
1. Initialize the staging database schema:
    ```bash
    $ ./bin/migrate_db ./config/db 0 marti_staging marti_dice
    ```

## Deploy application

In the following steps, `<dir>` refers to the deployment directory.  This will be `dice` for the production application and `dice-staging` for the staging application.

1. Login to `dice.tripleawarclub.org`.
1. Create the deployment directory if necessary.
    1. Create the directory:
        ```bash
        $ sudo mkdir /usr/share/nginx/html/tripleawarclub.org/public_html/<dir>/
        ```
    1. Change ownership:
        ```bash
        $ sudo chown www-data:www-data /usr/share/nginx/html/tripleawarclub.org/public_html/<dir>/
        ```
1. Change to the directory where you have cloned the `triplea-game/dice-server` repo.
1. Deploy the application:
    ```bash
    $ sudo -u www-data ./bin/deploy ./src/ /usr/share/nginx/html/tripleawarclub.org/public_html/<dir>/
    ```