# Docker crons

A docker container used to launch crons tasks easily

## Add a cron
Modify the crontab file and place your files into the ``/scripts`` folder

## Sample

``crontab``
```sh
* * * * * root /bin/sh /scripts/hello-world.sh >> /var/log/cron-stdout.log 2>&1
```

``/scripts/hello-world.sh``
```sh
echo "It works!"
```

This will print 'It works!' to the docker output

Skip the ``>> /var/log/cron-stdout.log 2>&1`` part in the crontab if you don't want the output to be seen in the container output (credentials, etc.)


## Bundled tools
Each of these can be of course removed from the container if you are not using them, in the Dockerfile.

### AWS CLI

Env vars to set on your container if you use the AWS CLI in your scripts
```sh
AWS_ACCESS_KEY_ID=<AWSaccessKey>
AWS_SECRET_ACCESS_KEY=<AWSsecretKey>
AWS_DEFAULT_REGION=<AWSregion>
```

### Tutum CLI
```sh
TUTUM_USER=<username>
TUTUM_APIKEY=<password>
```

### Docker Cloud CLI
```sh
DOCKERCLOUD_USER=<username>
DOCKERCLOUD_PASS=<password>
```

### Mongodb commands
```
mongodump     mongoexport   mongofiles    mongoimport   mongooplog
mongoperf     mongorestore  mongostat     mongotop 
```

### MySQL and MariaDB commands
```
mysql                 mysql_fix_extensions  mysqlaccess           mysqlanalyze
mysqlcheck            mysqldumpslow         mysqloptimize         mysqlreport
mysqlslap             mysql_find_rows       mysql_waitpid         mysqladmin
mysqlbug              mysqldump             mysqlimport           mysqlrepair
mysqlshow          
```

### Postgres commands
```
pg              pg_basebackup   pg_dump         pg_dumpall      pg_isready
pg_receivexlog  pg_recvlogical  pg_restore      pgbench         pgrep   
```

## Available scripts
To launch one of the following scripts, the env vars must be set

### MongoDB backup

Require AWS env vars
```
MONGO_DB_HOST=<host>
MONGO_DB_PORT=<port>
MONGO_DB_NAME=<database>
MONGO_DB_USER=<username>
MONGO_DB_PASS=<password>
MONGO_S3_REGION=<AWSS3Region>
MONGO_S3_BUCKET=<AWSS3Bucket>
```

### Postgres backup

Require AWS env vars
```
POSTGRES_HOST=<host> 
POSTGRES_PORT=<port>
POSTGRES_DB=<database>
POSTGRES_USER=<username>
POSTGRES_PASS=<password>
POSTGRES_S3_REGION=<AWSS3Region>
POSTGRES_S3_BUCKET=<AWSS3Bucket>
```

### MariaDB backup

Require AWS env vars
```
MARIADB_HOST=<host>
MARIADB_PORT=<port>
MARIADB_DB=<database>
MARIADB_USER=<username>
MARIADB_PASS=<password>
MARIADB_S3_REGION=<AWSS3Region>
MARIADB_S3_BUCKET=<AWSS3Bucket>
```

### SCP backup

Require AWS env vars
```
SCP_HOST=<host>
SCP_PORT=<port>
SCP_USER=<username>
SCP_PASS=<password>
SCP_FOLDER=<folder>
SCP_S3_REGION=<AWSS3Region>
SCP_S3_BUCKET=<AWSS3Bucket>
```

## Notifications

### Slack notifications

Send notifications to Slack
```
SLACK_WEBHOOK_URL=<SlackWebhookUrl>
```