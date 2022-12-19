


     1.ADMINER


```
https://hub.docker.com/_/adminer

 version: '3.1'
 services:

   adminer:
     image: adminer
     restart: always
     ports:
      - 8080:8080

   db:
     image: mysql:5.6
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: example


       
 - Primero creamos un archivo "docker-compose" copiamos lo que tenemos arriba 
  y luego usamos el comando -> docker-compose -f docker-compose.yml up.
  
```




```

2.GUESTBOOK

```

```
https://iesgn.github.io/curso_docker_2021/sesion5/guestbook.html

 version: '3.1'
services:
  app:
    container_name: guestbook
    image: iesgn/guestbook
    restart: always
    ports:
      - 80:5000
  db:
    container_name: redis
    image: redis
    restart: always
```



 - Primero creamos un archivo "docker-compose" copiamos lo que tenemos arriba  y luego usamos el comando -> docker-compose -f docker-compose.yml up.





 ```

3.MEDIAWIKI

```

```
https://hub.docker.com/_/mediawiki

         # MediaWiki with MariaDB
#
# Access via "http://localhost:8080"
#   (or "http://$(docker-machine ip):8080" if using docker-machine)
version: '3'
services:
  mediawiki:
    image: mediawiki
    restart: always
    ports:
      - 8080:80
    links:
      - database
    volumes:
      - images:/var/www/html/images
      # After initial setup, download LocalSettings.php to the same directory as
      # this yaml and uncomment the following line and use compose to restart
      # the mediawiki service
      - ./LocalSettings.php:/var/www/html/LocalSettings.php
  # This key also defines the name of the database host used during setup instead of the default "localhost"
  database:
    image: mariadb
    restart: always
    environment:
      # @see https://phabricator.wikimedia.org/source/mediawiki/browse/master/includes/DefaultSettings.php
      MYSQL_DATABASE: my_wiki
      MYSQL_USER: wikiuser
      MYSQL_PASSWORD: example
      MYSQL_RANDOM_ROOT_PASSWORD: 'yes'
    volumes:
      - db:/var/lib/mysql

volumes:
  images:
  db:
```



 - Primero creamos un archivo "docker-compose" copiamos lo que tenemos arriba  y luego usamos el comando -> docker-compose -f docker-compose.yml up.
 - Al final pide descargar un archivo y copiarlo en el contenedor;tengo que copiar el LocalSettings.php en la carpeta. Entonces, terminas usando el comando:
        ->docker cp ./LocalSettings.php mediawiki_mediawiki_1:/var/www/html.





 ```

4.SERVIDOR APACHE

```

```
https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/Simple-Apache-docker-compose-example-with-Dockers-httpd-image

 version: '3.9'
services:
  apache:
    image: httpd:latest
    container_name: my-apache-app
    ports:
    - '8080:80'
    volumes:
    - ./website:/usr/local/apache2/htdocs
```



 - Primero creamos un archivo "docker-compose" copiamos lo que tenemos arriba  y luego usamos el comando -> docker-compose -f docker-compose.yml up.




  ```

5.WORDPRESS

```

```
https://hub.docker.com/_/wordpress

 version: '3.1'

services:

  wordpress:
    image: wordpress
    restart: always
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: exampleuser
      WORDPRESS_DB_PASSWORD: examplepass
      WORDPRESS_DB_NAME: exampledb
    volumes:
      - wordpress:/var/www/html

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_DATABASE: exampledb
      MYSQL_USER: exampleuser
      MYSQL_PASSWORD: examplepass
      MYSQL_RANDOM_ROOT_PASSWORD: '1'
    volumes:
      - db:/var/lib/mysql

volumes:
  wordpress:
  db:
```



 - Primero creamos un archivo "docker-compose" copiamos lo que tenemos arriba  y luego usamos el comando -> docker-compose -f docker-compose.yml up.












        


