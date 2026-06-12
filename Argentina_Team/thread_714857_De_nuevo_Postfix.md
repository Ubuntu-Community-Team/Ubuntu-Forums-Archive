---
title: "De nuevo Postfix"
date: 2008-03-04
forum: Argentina Team
---

### Post by zergiomp on 2008-03-04
Buenas!
Antes de nada, deciros que mis conocimientos de Linux son muy precarios.
De nuevo vuelvo a postear sobre la instalacion de postfix, por que avance mediante un documento que encontre, pero ahora tengo algunas dudas mas.Para los que no leyesen mi anterior mensaje en el foro,mi objetivo es el siguiente. Debo instalar Moodle en una máquina y ademas, integrarle un servidor de correos antispam. Instalé Moodle y supuestamente me funciona bien. Puedo entrar con los usuarios que e creado y tal, autenticandome desde la misma máquina. Y ademas puedo crear cursos, etc, etc...Lo instale guiandome por estas dos páginas:

[http://docs.moodle.org/es/Instalaci%C3%B3n_de_moodle#Requerimientos](http://docs.moodle.org/es/Instalaci%C3%B3n_de_moodle#Requerimientos)
[http://www.ubuntu-es.org/index.php?q=node/53465](http://www.ubuntu-es.org/index.php?q=node/53465)

Os dejo aqui la configuración de varios archivos de la instalación de moodle para que le echeis un ojo:


config.php:
dbtype = 'mysql';
$CFG->dbhost = 'localhost';
$CFG->dbname = 'moodle';
$CFG->dbuser = 'moodleus';
$CFG->dbpass = '875421986532'
;$CFG->dbpersist = false;
$CFG->prefix = 'mdl_';
$CFG->wwwroot = 'http://127.0.0.1/moodle';
$CFG->dirroot = '/var/www/moodle';
$CFG->dataroot = '/var/www/moodledata';
$CFG->admin = 'admin'; $CFG->directorypermissions = 00777; // try 02777 on a server in Safe Mode
require_once("$CFG->dirroot/lib/setup.php");
// MAKE SURE WHEN YOU EDIT THIS FILE THAT THERE ARE NO SPACES, BLANK LINES,
// RETURNS, OR ANYTHING ELSE AFTER THE TWO CHARACTERS ON THE NEXT LINE.
?>



httpd.conf:
AddType application/x-httpd-php .php
DirectoryIndex index.php index.html index.htm
AcceptPathInfo on


(El archivo php.ini esta configurado tal como viene en el primer enlace que os dejo y la base de datos MOODLE, tal como pone en el segundo enlace)

Bueno, una vez explicado todo esto, nos iremos a la instalación del servidor de correos. Elegi postfix, guiandome por el manual del siguiente enlace que os dejo:

[http://doc.ubuntu-es.org/Postfix/configuración_de_un_servidor_incluyendo_Postfixadmin%2C_Mysql%2C_Spamassassin_y_ClamAv](http://doc.ubuntu-es.org/Postfix/configuración_de_un_servidor_incluyendo_Postfixadmin%2C_Mysql%2C_Spamassassin_y_ClamAv)

Y mi pregunta es, la instalación que se hace de Postfix, ¿¿es una instalacion de un servidor para una red local??Es decir, sin salida de los correos a internet. Yo solo necesito que los correos lleguen a los usuarios de esa red local. Y aqui me surge mi siguiente duda. En la instalación de Postfix se crea una base de datos, pero no se para que va a servir esa base de datos y claro, se supone que los usuarios que debe administrar Postfix, son los usuarios de Moodle (la cual, ya tiene una base de datos tambien) ¿¿Que se supone que tengo que hacer?? ¿¿Como vinculo los usuarios creados en moodle, con postfix?? La verdad, que ando algo perdido y necesito ayuda con esto, por que no encuentro informacion sobre lo que necesito hacer.

¿Algun alma caritativa para ayudar a esta pobre oveja descarriada? ¿Alguien con ganas de superarse, en busca de retos? ¿Algun/a sabi@ sobrado de sabiduria que me eche un cable?

Muchisimas gracias por leerme y un cordial saludo a tod@s!!!

---

