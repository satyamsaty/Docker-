# Docker
Docker related files

version: '3'
services:
  dbos:
    image: mysql:5.7
    volumes:
      - mysql_storage_new:/var/lib/mysql
    restart: always

    environment:
       MYSQL_ROOT_PASSWORD: mysql
       MYSQL_USER: satyam
       MYSQL_PASSWORD: mysql
       MYSQL_DATABASE: mydb


  wordpressos:
    image: wordpress:5.1.1-php7.3-apache
    restart: always
    ports:
      - 8081:80
    depends_on:
      - dbos
    volumes:
      -  wp_storage_new:/var/www/html

    environment:
       WORDPRESS_DB_HOST: dbos
       WORDPRESS_DB_USER: satyam
       WORDPRESS_DB_PASSWORD: mysql
       WORDPRESS_DB_NAME: mydb

volumes:
   mysql_storage_new:
   wp_storage_new:

