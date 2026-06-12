---
title: "Otra pregunta y van...."
date: 2007-09-20
forum: Argentina Team
---

### Post by vk-cdg on 2007-09-20
Tengo la siguiente situacion y quería ver cual es el consejo de ustedes que seguro tienen mas experiencia que yo.

Tengo mi PC de casa con un disco SATA de 250GB en donde actualmente tengo instalado el Win XP. El disco está casi lleno de cosas importantes y otras no tanto, música, películas, etc. que no me gustaría perder ya que si bien no son importantes, volver a bajarlas no me simpatiza demasiado.

Como conté en otro post, llegó el disco SATA de 160Gb en el cual voy a instalar Win XP en una partición y Ubuntu en la otra haciendo dos iguales de 80 cada una.
El disco de 250 va a quedar para que contenga solamente los datos, pero actualmente tiene partición NTFS.
La idea de todo esto es poder ver, desde cualquiera de los dos SO los mismos datos. Si bien mi idea no es usar Win, mi mujer si lo va a usar y la música y pelis son compartidas.

Tengo ciertas dudas con temas como:

¿que hago con la partición home? ¿que me conviene? 
Si la pongo en el otro disco, desde wind*ws no la puedo ver.

Me conviene dejar el otro disco en NTFS e instalar el complemento para que UBUNTU escriba sobre ese tipo de partición o la paso a FAT?

Existe forma de que la carpeta personal esté apuntada a otro disco? Se que "Dócuments and Settings" lo puedo mover. De hecho mi idea era moverlo al disco de datos. Tenía ganas de hacer algo similar con Ubuntu para que el disco de 160 sea solo de sistemas operativos y progeamas, si hay que formatear se hace sin pensar en que me olvido de backapear.

Bueno, disculpas por el post largo, pero medio que me desconsertó el tema, y mas el tema de no saber como mover los datos de un lado para el otro (bajar 190GB de datos a DVD me va a llevar un rato. :(

Muchas gracias de antemano por su ayuda!

---

### Post by MatoGroso on 2007-09-20
> **vk-cdg said:**
> Tengo la siguiente situacion y quería ver cual es el consejo de ustedes que seguro tienen mas experiencia que yo.

Tengo mi PC de casa con un disco SATA de 250GB en donde actualmente tengo instalado el Win XP. El disco está casi lleno de cosas importantes y otras no tanto, música, películas, etc. que no me gustaría perder ya que si bien no son importantes, volver a bajarlas no me simpatiza demasiado.

Como conté en otro post, llegó el disco SATA de 160Gb en el cual voy a instalar Win XP en una partición y Ubuntu en la otra haciendo dos iguales de 80 cada una.
El disco de 250 va a quedar para que contenga solamente los datos, pero actualmente tiene partición NTFS.
La idea de todo esto es poder ver, desde cualquiera de los dos SO los mismos datos. Si bien mi idea no es usar Win, mi mujer si lo va a usar y la música y pelis son compartidas.

Tengo ciertas dudas con temas como:

¿que hago con la partición home? ¿que me conviene? 
Si la pongo en el otro disco, desde wind*ws no la puedo ver.

Me conviene dejar el otro disco en NTFS e instalar el complemento para que UBUNTU escriba sobre ese tipo de partición o la paso a FAT?

Existe forma de que la carpeta personal esté apuntada a otro disco? Se que "Dócuments and Settings" lo puedo mover. De hecho mi idea era moverlo al disco de datos. Tenía ganas de hacer algo similar con Ubuntu para que el disco de 160 sea solo de sistemas operativos y progeamas, si hay que formatear se hace sin pensar en que me olvido de backapear.

Bueno, disculpas por el post largo, pero medio que me desconsertó el tema, y mas el tema de no saber como mover los datos de un lado para el otro (bajar 190GB de datos a DVD me va a llevar un rato. :(

Muchas gracias de antemano por su ayuda!

Hola! Si instalas en el HD de 160 los 2 SO, con cualquiera vas a poder ver el otro disco NTFS.

---

### Post by leonelb on 2007-09-20
Pq no instalás todo Linux en el nuevo disco, incluyendo a /home, y luego creás dentro de /home una carpeta llamada docs o lo que quieras, y montás el disco con tus datos en esa carpeta? De esa forma tendrías acceso a los archivos que ya tenés en el disco viejo sin tocarlo. Sólo tendrías que tener cuidado de guardar cualquier nuevo documento tuyo dentro de esta carpeta /home/docs.

Saludos
Leonel

---

### Post by leonelb on 2007-09-20
Perdón, recién puse como carpeta /home/docs, pero quise poner /home/usuario/docs. A eso me refería

Saludos
Leonel

---

### Post by vk-cdg on 2007-09-20
El tema es que desde XP mi mujer no va a poder ver los archivos con los que yo trabaje en Ubuntu.

Por otro lado la idea de tener 2 discos era que uno fuera solo para instalaciones, cosa que si tengo que formatear, lo hago sin pensar si me olvido algo. 
En el otro disco tendría los perfiles de XP y de Ubuntu mas los archivos de trabajo, musica y videos.

---

### Post by FlyerDie on 2007-09-20
> **vk-cdg said:**
> El tema es que desde XP mi mujer no va a poder ver los archivos con los que yo trabaje en Ubuntu.

Por otro lado la idea de tener 2 discos era que uno fuera solo para instalaciones, cosa que si tengo que formatear, lo hago sin pensar si me olvido algo. 
En el otro disco tendría los perfiles de XP y de Ubuntu mas los archivos de trabajo, musica y videos.

Si que va a poder ;)
Instalate en el windows IFS Drives ( [http://www.fs-driver.org/](http://www.fs-driver.org/) ) y vas  a poder acceder a partisiones ext2/ext3 desde windows :guitar:

---

### Post by leonelb on 2007-09-21
Lo que yo decía es dejar el disco de 160 en NTFS, con tus documentos y los de tu mujer. Instalás XP y Ubuntu en el nuevo disco, y en Ubuntu habilitás el módulo para escribir en unidades NTFS. La carpeta /home de Ubuntu la dejás instalada en el nuevo disco, pero dentro de esta carpeta  , en tu carpeta de usuario, creás otra llamada Docs, y montás todo el disco viejo en esta carpeta. El disco es NTFS, y vas a poder acceder vos y tu mujer cuando use XP.

Espero haber sido claro
Saludos
Leonel

---

### Post by vk-cdg on 2007-09-21
Eso es lo que yo pensé en un principio, pero no sabía (no muchos me lo confirmaron) que tan bien funciona la escritura en NTSF. Imagino que si Gusty lo trae de serie debe estar bien probado.

Entonces, a ver si entendí.

- Disco viejo (el mas grande) 250 GB para datos, lo dejo en NTFS
- Disco nuevo (dos particiones) en una instalo XP y en la otra Ubuntu

Lo que no me queda claro, mejor dicho, no se como hacer, es montar dentro de mi carpeta /home/vikingo el otro disco.

---

### Post by FlyerDie on 2007-09-21
> **vk-cdg said:**
> Eso es lo que yo pensé en un principio, pero no sabía (no muchos me lo confirmaron) que tan bien funciona la escritura en NTSF. Imagino que si Gusty lo trae de serie debe estar bien probado.

Entonces, a ver si entendí.

- Disco viejo (el mas grande) 250 GB para datos, lo dejo en NTFS
- Disco nuevo (dos particiones) en una instalo XP y en la otra Ubuntu

Lo que no me queda claro, mejor dicho, no se como hacer, es montar dentro de mi carpeta /home/vikingo el otro disco.


en vez de el punto de montado (que feo suena) sea en /mnt/LOQUEQUIERAS lo pones en /home/vikingo/MIMUJER .. entendes?

---

### Post by mpbe on 2007-09-22
Yo haria lo siguiente, en el disco nuevo haria 2 particiones, / y /home. Dejaria windows donde esta y cambiaria la particion nfts de documentos compartidos la cambiaria a ext3 (con gparted live), en linux la montas en /media/loquesea o /mnt/loquesea y desde windows accedes con ifs ([http://www.fs-driver.org/](http://www.fs-driver.org/))

---

### Post by undiaperfecto on 2007-09-23
esto ultimo es lo mejor me parece.

disco nuevo mitad xp, otra mitad ubuntu
disco viejo, datos, formato ext3

instalas el driver para windows para que lea ext3 y listo
el driver es facilisiiiiiiiimo de usar

---

