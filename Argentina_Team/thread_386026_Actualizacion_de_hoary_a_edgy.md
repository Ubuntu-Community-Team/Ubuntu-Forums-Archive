---
title: "Actualizacion de hoary a edgy"
date: 2007-03-16
forum: Argentina Team
---

### Post by fetova on 2007-03-16
hola! A un amigo le pedi que me hiciera el favor con mi lap, pues le vole las particiones, me puso el ubuntu 5.04, extraño a edgy, asi que la quiero actualizar. Mi pregunta es... ¿puedo actualizar de un solo golpe o como le puedo hacer?

muchas gracias :)

---

### Post by marianom on 2007-03-16
Primero tenes que actualizar a 5.10 (Breezy). [Aca]("https://help.ubuntu.com/community/BreezyUpgradeNotes") está la guía.

Luego a dapper según [esta guía]("https://help.ubuntu.com/community/DapperUpgrades").

---

### Post by fetova on 2007-03-16
Gracias, voy a intentar la actualizacion el fin de semana

luego cuento como me fue [-o< (ojala bien)

---

### Post by ubuntu27 on 2007-03-18
> **fetova said:**
> Gracias, voy a intentar la actualizacion el fin de semana

luego cuento como me fue [-o< (ojala bien)

Como marianom dijo primero debes de actualizar tu Ubuntu 
desde Hoary a Breezy, de Breezy a Dapper, y de Dapper a Edgy.


Pero, dudo que lo logres sin problemas. 
Te recomiendo que te bajes el iso de Edgy Eft (Ubuntu 6.10), quemarlo en un CD como imagen, y instalr Ubuntu encima de tu viejo Ubuntu.

---

### Post by DuckMan on 2007-03-19
no solo te conviene, casi estas obligado xD vas a matar a los servidores de ubuntu..

bajate el edgy y quemalo, va a ser mucho mas practico

---

### Post by lavaramano on 2007-03-20
> **DuckMan said:**
> no solo te conviene, casi estas obligado xD vas a matar a los servidores de ubuntu..

bajate el edgy y quemalo, va a ser mucho mas practico

secundo la mocion.
aunque te diria que primero backupees al home, como se suele recomendar.

---

### Post by fetova on 2007-03-20
> **ubuntu27 said:**
> 


Pero, duda que lo logres sin problemas. 


....
ya lo note :( el teclado lo reconoce... pero no tipea nada, me paso consola con ctrl+alt+F1 y ahi si se ve que entran las letras pero la pantalla se ve a medias, solo la parte de arriba :( 

ayudaaaaaaa :(

se me hace que voy buscar una unidad de cd y voy a instalar encima............

---

### Post by beuno on 2007-03-20
> **fetova said:**
> ....
ya lo note :( el teclado lo reconoce... pero no tipea nada, me paso consola con ctrl+alt+F1 y ahi si se ve que entran las letras pero la pantalla se ve a medias, solo la parte de arriba :( 

ayudaaaaaaa :(

se me hace que voy buscar una unidad de cd y voy a instalar encima............

Eso fue un bug con los teclados "lat".

Tenes dos opciones:

Ponerlo en "es" y despues cambiar de Gnome.

o, no me acuerdo si ya funcionaba para ese momento, "latam".

Esto es en /etc/X11/xorg.conf

---

### Post by fetova on 2007-03-20
> **beuno said:**
> Eso fue un bug con los teclados "lat".

Tenes dos opciones:

Ponerlo en "es" y despues cambiar de Gnome.

o, no me acuerdo si ya funcionaba para ese momento, "latam".

Esto es en /etc/X11/xorg.conf

Gracias, pero... Como edito desde consola? gedit no sirve ahi....:confused:

EDITED: ya encontre nano :)

---

### Post by fetova on 2007-03-20
> **DuckMan said:**
> no solo te conviene, casi estas obligado xD vas a matar a los servidores de ubuntu..

bajate el edgy y quemalo, va a ser mucho mas practico

creo comprender... casi mil paquetes!!!!!!!! para UNA actualizacion :???:

---

### Post by beuno on 2007-03-20
> **fetova said:**
> creo comprender... casi mil paquetes!!!!!!!! para UNA actualizacion :???:

Yo creo que debe actualizar el 95% de los paquetes.
Pensa que las versiones de Ubuntu no son al azar, es por cargar todas las actualizaciones de todos los paquetes.
Por otro lado, la gente que esta en open source tiene a ser muy movediza, asi que se hacen muchas cosas en 6 meses.

---

### Post by fetova on 2007-03-20
> **beuno said:**
> Yo creo que debe actualizar el 95% de los paquetes.
Pensa que las versiones de Ubuntu no son al azar, es por cargar todas las actualizaciones de todos los paquetes.
Por otro lado, la gente que esta en open source tiene a ser muy movediza, asi que se hacen muchas cosas en 6 meses.

eso si... es lo lindo de esto...
libre...
libre de hacer lo que quieras...
y te ayudan :)

---

### Post by lavaramano on 2007-03-20
no confundamos open source con free software o terminamos todos a las piñas (?)
nah, mentira. :lolflag:

---

### Post by fetova on 2007-03-20
ahhhhhhhhhhhhhhh:mad: :mad: 

Para subir a dapper ya no sale cuando ejecuto  "sudo apt-get update && sudo apt-get dist-upgrade " se quiere conectar, pero no puede!!!

Ayudaa, ya configure red, ya cambie el sources.list..... :( son padres los retos, pero......

---

### Post by fetova on 2007-03-22
Tengo un pequeño problema, me quede trabado en breezy, los paquetes de synaptic no cargan
 :( 

los errores son:

[HTML]E: Error de lectura - read (21 Es un directorio)
E; Problem opening /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dist_dapper_main_binary-i386_Packages
E: Las listas de los paquetes o el archivo de estado no se pueden analizar sintacticamente o abrir[/HTML]

muchas graxias

---

### Post by strugart on 2007-03-22
Se te jodio un par de bits y el synaptic murio (osea tenes que cambiar de version por live cd no hay otra forma).  Es solo una version...

---

### Post by fetova on 2007-03-26
> **strugart said:**
> Se te jodio un par de bits y el synaptic murio (osea tenes que cambiar de version por live cd no hay otra forma).  Es solo una version...

pues ojala no.:(

Pero cuando menos ya no jala gnome:(

en serio voy a tener que reinstalar?

---

### Post by strugart on 2007-03-26
Si se te jodio gnome...me parece que si...

---

### Post by fetova on 2007-03-29
\\:D/ \\:D/ \\:D/ 

ya estoy en dapper!! :popcorn: 

Un amigo me ayudo aqui y ya esta!!!

Gracias por todo :D

---

