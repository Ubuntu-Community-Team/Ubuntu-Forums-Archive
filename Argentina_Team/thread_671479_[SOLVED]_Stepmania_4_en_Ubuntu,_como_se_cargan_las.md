---
title: "[SOLVED] Stepmania 4 en Ubuntu, como se cargan las canciones?"
date: 2008-01-18
forum: Argentina Team
---

### Post by atari130xe on 2008-01-18
Ahora que logré la aceleración grafica en mi PC estoy probando algunas cosas entre ellas un par de juegos, me metí en [http://www.getdeb.net]("http://www.getdeb.net") y bajé Stepmania4 todo bien el programa funciona muy bien, pero.... NO puedo cargarle las canciones. Según las MUY escuetas instrucciones del sitio oficial dice que hay que descomprimir las canciones en la carpeta (oculta) ./stepmania4/songs (que está en mi home) pero... ya intenté de todo y no hay caso no carga ninguna canción, alguién que haya incursionado en ese juego, sabe como hacerlo paso a paso? :confused:

---

### Post by marianom on 2008-01-18
Soy lo menos gamer del mundo así que pregunto una obviedad... ¿tenes permisos de lectura y/o ejecución (creo que solo el primero es necesario pero por las dudas lo menciono)?

---

### Post by atari130xe on 2008-01-18
jejeje yo tampoco soy lo mas gamer del mundo, lo que más puedo usar de vez en cuando es el Xmame jejeje, mirá imagino algo de eso, pero no recuerdo como darle los permisos al archivo "chmod" es, no? o sea tengo el archivo:

Songs_DJMcFox_PlagueMixOne.smzip  es una de las canciones (en formato propio del programa pero que con el gestor de archivadores funca bien). seria...

sudo chmod +x Songs_DJMcFox_PlagueMixOne.smzip ?

Hace mil que no hago eso!

---

### Post by marianom on 2008-01-18
Para no frustrarte de antemano, hace un 
```
ls -l 
```
sobre el contenido del directorio así vemos si eso es un problema.

---

### Post by atari130xe on 2008-01-18
Vos decis el directorio de destino? o donde tengo el archivo a descomprimir?

---

### Post by marianom on 2008-01-18
Sobre el destino, una vez estás descomprimidas.

---

### Post by atari130xe on 2008-01-18
```
jose@jose-desktop:~/.stepmania4/Songs$ ls -l
total 8
drwxrwx--- 3 jose jose 4096 2008-01-18 21:10 Songs_DJMcFox_HappyTheme.smzip_FILES
drwxrwx--- 3 jose jose 4096 2008-01-18 17:33 Songs_DJMcFox_PlagueMixOne.smzip_FILES
jose@jose-desktop:~/.stepmania4/Songs$
```

el sitio oficial:

[http://www.stepmaniawiki.com/wiki/FAQ_and_Tutorials]("http://www.stepmaniawiki.com/wiki/FAQ_and_Tutorials")

---

### Post by Mauro22 on 2008-01-18
[http://www.stepmaniawiki.com/wiki/Download_Songs](http://www.stepmaniawiki.com/wiki/Download_Songs)

Ahi hay canciones para ese juego, talvez no podes agegar cualquiera

---

### Post by atari130xe on 2008-01-18
no habla de restricciones en las canciones, es raro :confused:

---

### Post by Mafber on 2008-01-18
Por ej. si te bajas la canción "BlowMeUp" (Songs_StepMix1_Taren_BlowMeUp.smzip) descomprimila y te va a quedar algo así:
/home/mafber/**.stepmania4/Songs/StepMix 1.0/Blow Me Up**
Las canciones estan divididas en:
StepMix 1.0
StepMix 2
StepMix 3
Dentro de estos directorios van las carpetas de las canciones que te bajas.
Suerte!!!

---

### Post by atari130xe on 2008-01-19
Puedo preguntarte el procedimiento para descomprimir las canciones al directorio ./stepmania4/songs ? o sea lo descomprimís haciendo "doble click" o lo hacés por consola? me podrias explicar porfis? 
Lo que explicaste es maso lo que vengo probando pero cuando inicio el programa me dice 0 canciones etc etc (parte izq de la pantalla arriba) le doy a recargar canciones y sigue en 0 por eso te digo, es probable que sea algun tema de la carpeta oculta y los permisos, no lo sé.

---

### Post by Mafber on 2008-01-19
Hola, hacé boton derecho sobre el archivo y "descomprimir aqui" te va a crear una carpeta "Song" y dentro la carpeta "StepMix XXX" (X es el numero). Copia desde este última dirctorio y pegalo dentro de:
/.stepmania4/Songs
te tine que quedar de esta manera:
/home/TU-USUARIO/.stepmania4/Songs/StepMix 1.0/Blow Me Up
donde Blow Me Up es el nombre de la canción que bajaste

---

### Post by atari130xe on 2008-01-19
Al fin pude cargar al menos 2 canciones, es como tomar un curso para ir a marte :lolflag:, de verdad creo que algunos programas tienen explicaciones muy endebles, porque sinceramente podria aclarar el punto desde DONDE copiar los archivos, dice: "descomprimir los archivos a la carpeta home/.stepmania4/songs/" PERO NO DICEN DESDE QUE ARCHIVO :), aura si, solo es curiosidad pero... que laburo jejeje. gracias!

PD: Leía hace un rato en un post de Gnomelook.org por la instalación de unos screenlets: "Porque algunos complican TANTO las cosas no siendo claros con las instrucciones sobre instalar algo, todo lo que no sea detallado va a acarrear preguntas y re preguntas hasta que la instalación sea realizada exitosamente, dando por echo que el grueso de la gente sabe hacerlo, cuando eso no es así" taba re cabreado el "cristiano" -supuesta programador de Linux o algo por el estilo-

---

### Post by Mafber on 2008-01-19
Me alegro que hayas podido hacer que funcione. Fijate bien esto de los carpetas "StepMix 1.0", no se si se pueden mezclar, poner un tema de "StepMix 1.0" dentro del directorio de "StepMix 2". Nunca probé
El juego es muy bueno y se puede jugar de a dos en modo cooperativo o en contra.

Coincido en que algunas ayudas no ayudan :-k ja Para entender como poner las caniones tardé un buen rato y no pude... hasta que llegó un amigo y entre los dos logramos que funque
Suerte!!! :)

---

