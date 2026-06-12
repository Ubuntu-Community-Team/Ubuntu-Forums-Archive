---
title: "Error al crear base con  mysql"
date: 2007-08-20
forum: Argentina Team
---

### Post by aceki on 2007-08-20
Gente buenas noches, los molesto como siempre, les cuento, luego de buscar y buscar encontre un tutorial para armar un servidor de mail con postfix mysql y courier ([http://tuxedlinux.wordpress.com/2007/07/27/servidor-de-correo-postfix-con-courier-y-soporte-mysql/](http://tuxedlinux.wordpress.com/2007/07/27/servidor-de-correo-postfix-con-courier-y-soporte-mysql/))

Bueno instale el postfix, configure todo bien, ahora cuando voy a crear la base en mysql, (fijecen en el tutorial que dice como hacer) me manda este error cuando pongo esta sentencia:

root@loki:/home/aceki#  _mysql -h localhost -u root -p_
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
root@loki:/home/aceki#

Tambien intente con sudo (medio al ****, ya que uso el roor directamente), alguien que me ayude ya que me quede sin servidor de correo, gracias a todos!!!

---

### Post by tzulberti on 2007-08-21
Para conectarte lo correcto es: 
mysql -h localhost -u root

Saludos,
TZ

---

### Post by faktorqm on 2007-08-21
Hola, te comento algo que no tiene nada que ver con el post. 
Linux está pensado para usar el usuario root pura y exclusivamente cuando es absolutamente necesario. Teóricamente NO deberías usar el usuario root, por que podés romper todo, sin saberlo obviamente. Un usuario "sudoer" NO es igual que el usuario root, al contrario de lo que piensa el 99,99% de la gente. Te lo comento para que de ahora en mas trates de usar sudo en lugar de root para tareas administrativas, es más seguro para la estabilidad de tu sistema. (hablo de estabilidad a nivel ser humano :P) We, solo un consejo. si ya lo sabias perdona por hacerte leer ;)

---

### Post by aceki on 2007-08-21
faktorqm quien te pensas que sos para hablarme asi!!!... no mentira, la verdad pense que el su y el root eran el mismo, tenes razon, use el root por que me saltava el el ejemplo del tutorial, gracias por las explicacion.. por algo el ubuntu trae el root desavilitado :lolflag:

tzulbert, gracias ahi entro ahora me manda esto:

create table passwd(
id char ( 128 ) DEFAULT &#8221; NOT NULL,
clear char ( 128 ) DEFAULT &#8221; NOT NULL,
name char ( 128 ) DEFAULT &#8221; NOT NULL,
uid int ( 10 ) unsigned NOT NULL,
gid int ( 10 ) unsigned NOT NULL,
home char ( 255 ) DEFAULT &#8221; NOT NULL,
maildir char ( 255 )DEFAULT &#8221; NOT NULL,
KEY id (id ( 128 ))
);

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '&#8221; NOT NULL, clear char(128)DEFAULT &#8221; NOT NULL, name char(128)DEFAULT &#8221; NOT' at line 

Es raro por que copie todo tal cual la pagina, que puede ser

---

### Post by marianom on 2007-08-21
O te sobran o te faltan comillas dobles alrededor del NOT NULL.

---

### Post by facundocorradini on 2007-08-21
dos cosas:

1) creo q lo del principio no andaba pq te pedía la contraseña del usuario root de mysql, no el del root del sistema (y mucho menos el de tu usuario sudoer)

2) en esa consulta sobran comillas. Borrá las comillas dobles que están antes de NOT NULL

y semi-off-topic: para qué estás armando un servidor de mail?

---

### Post by aceki on 2007-08-21
para un empresa de 30 usuario que nesecitan mail, ya le migre todas la pc a ubuntu, y bueno no queria dejar el servidor con windows, pero me parece que va a quedar, por que cada vez entiendo menos por que no me andan las cosas en ubuntu!!!

---

### Post by tzulberti on 2007-08-21
> **aceki said:**
> 
create table passwd(
id char ( 128 ) DEFAULT &#8221; NOT NULL,
clear char ( 128 ) DEFAULT &#8221; NOT NULL,
name char ( 128 ) DEFAULT &#8221; NOT NULL,
uid int ( 10 ) unsigned NOT NULL,
gid int ( 10 ) unsigned NOT NULL,
home char ( 255 ) DEFAULT &#8221; NOT NULL,
maildir char ( 255 )DEFAULT &#8221; NOT NULL,
KEY id (id ( 128 ))
);


El error esta en este campo:
Key id id (id ( 128 ))

que deberia de ser:
Primary Key (id)

ademas, no se pueden usar comillas dobler, solo se pueden usar comillas simples. Lo que vos estas intentando de hacer deberia de quedarte asi:
create table passwd(
id char ( 128 ) DEFAULT'' NOT NULL,
clear char ( 128 ) DEFAULT '' NOT NULL,
name char ( 128 ) DEFAULT '' NOT NULL,
uid int ( 10 ) unsigned NOT NULL,
gid int ( 10 ) unsigned NOT NULL,
home char ( 255 ) DEFAULT '' NOT NULL,
maildir char ( 255 )DEFAULT '' NOT NULL,
PRIMARY KEY(id)
);

NOTA: no se si es por algo del copy&paste, pero las " deberian de ser dos ' .

Espero haberte sido de ayuda.

---

### Post by marianom on 2007-08-21
tzulberti, de ser como vos decís, para qué estarían las ''? Entiendo si el default es un espacio en blanco, lo que sería ' ' pero en el caso que presentás no están poniendo nada como default? (Y eso tampoco explica el NOT NULL posterior).

La subjetiva impaciencia que le tengo al mysql puede ser que no me permita ver algo obvio,

---

### Post by facundocorradini on 2007-08-22
> **marianom said:**
> 

La subjetiva impaciencia que le tengo al mysql puede ser que no me permita ver algo obvio,

y eso que no lo trabajás a diario....

----------------------------------------

La verdad es que esas comillas no tienen razón de ser. simplemente deberías eliminarlas...

y el campo id, supongo que debería llevar AUTO_INCREMENT, 
y abajo debería decir PRIMARY KEY en vez de KEY....

------------------------------------------

Volviendo a lo práctico, por qué no te instalás una interfaz gráfica para mysql, como phpMyAdmin ?....

---

### Post by tzulberti on 2007-08-22
Tambien tenes MySql Admin, y MySQl Browser como GUIs para manejar la base de datos.

Sobre las comillas, tienen razon... No me puse a pensan en eso, sino que mas bien busque porque estaba el error de la cracion de la BD.

---

