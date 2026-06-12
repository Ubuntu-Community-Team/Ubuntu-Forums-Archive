---
title: "problemas con TEG"
date: 2007-05-03
forum: Argentina Team
---

### Post by zspikes on 2007-05-03
buenas foro!!! A ver si me pueden ayudar con esto?
Instale el TEG en feisty y estube jugando con unos amigos, la cosa es q me pinto tocar la configuracion, y le puse esa opcion de q salga el chat en colores (no se si tiene algo q ver)

La cosa es q no me abrio mas, y cdo pruebo abrirlo de consola me sale esto :S

x@x:~$ tegclient
I/O warning : failed to load external entity "themes//teg_theme.xml"
I/O warning : failed to load external entity "/home/gera/.teg//themes//teg_theme.xml"
I/O warning : failed to load external entity "/usr/share/games/teg/pixmaps/teg_pix/themes///teg_theme.xml"
Unable to load theme `'
Error loading theme!
Aborting...

He probado de todo, purgarlo y reinstalarlo, tocar los themes, TODO! y nada funciona :( alguna sugerencia? de ultima, a donde puedo poner las quejas? n_n

gracias!!!!

---

### Post by jayflower on 2007-05-04
Están los dirs esos ? /home/gera/.teg//themes//teg_theme.xml
Si no te los paso... y los copias ahi de nuevo... se habran corrompido los xml?

---

### Post by Al_maverick on 2007-05-04
yo borraria directamente la carpeta /home/gera/.teg, con eso eliminas la configuracion de tu usuario, que por lo que contas es lo que cambiaste y te trajo problemas.

ademas que hay algo raro, porque /home/gera/.teg**//**themes**//**teg_theme.xml no es exactamente una ruta correcta.

---

### Post by zspikes on 2007-05-04
ni idea che... probe borrar el .teg de mi carpeta local, probe purgarlo y reinstalarlo (no me reten)... borre los repos y lo volvi a bajar... TODO!! y nada parece funcionar :(
jayflower, te molestaria pasarme los archivos asi los piso y veo q onda?

gracias!

---

### Post by jayflower on 2007-05-04
No tengo nada dentro de las carpetas... donde tocaste? que raro :? a mi también me pasan esas cosas... PM a ver si te puedo dar una mano

---

### Post by zspikes on 2007-05-05
bueno, les cuento q ya lo solucionamos :P estube toda una noche con los muchachos de lugmen viendo q onda.
Les comento como lo solucione porq fue rarisimo jeje.
1-Copie el archivo teg_theme.xml q me paso un amigo en el directorio .teg
2-Ejecute esta linea q me pasaron q no tengo idea q hace jeje: $ for file in ~/.teg/themes/m2/*; do ln -s "$file" ~/.teg/themes; done; tegclient

Santo remedio :P gracias a todos por el apoyo! hasta luego!!!

---

