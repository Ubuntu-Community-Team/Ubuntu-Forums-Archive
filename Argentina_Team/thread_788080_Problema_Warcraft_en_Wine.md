---
title: "Problema Warcraft en Wine"
date: 2008-05-09
forum: Argentina Team
---

### Post by chispachips on 2008-05-09
Hola a todos.

Hace poco intenté instalar el World of Warcraft siguiendo todas las guías posibles, pero no consigo hacerlo funcionar, siempre me ocurre lo mismo. Cuando intento lanzar el juego se me queda la pantalla en negro excepto el cursor que es lo único que se muestra (el cursor del warcraft que es una mano). Es una instalación copiada de la de Windows pues en windows la misma me funciona bien, pero no me coje la conexión inalámbrica bien y se me desconecta entonces del servidor, y de ahí veo mi necesidad a hacerlo desde Ubuntu que sí me va la conexión; aunque lo he intentado tanto en una instalación de Windows como en una nueva desde el propio Wine.

He probado a poner de todo en el config de la carpeta WTF, poniendo SET gxApi "opengl", "directx", "d3d", pero nada... además intenté hacerlo desde la terminal escribiendo: wine wow.exe -opengl , y nada; de hecho poniendo esto último con "-opengl" me aparece un "Fatal error" más grave.. así que no sé; tengo la aceleración gráfica bien instalada; uso una ATI x1200 y tengo la versión 0.5.9 de Wine; uso Ubuntu Hardy Heron. ¿Alguién me puede echar un cable? :confused:

Gracias

---

### Post by margori on 2008-05-09
Lo has instalado sobre una partición ext3. A mi me fallan casi todos los programas que están instalados en NTFS.

Por otro lado, fijate si podes ponerle un parche No-CD, es decir, que no realice la búsqueda del CD en la ejecución.

Ejecuta un programa simple que use use DirextX o OpenGL y verificarias si hay problema entre Wine - DirectX - Ubuntu.

---

### Post by chispachips on 2008-05-10
Gracias por tu respueta. Esta última vez lo probé a arrancar desde la partición NTFS de Windows directamente (desde su instalación, sin moverlo); y como otra vez lo intenté instalando el juego desde 0 en Wine pues también lo intenté por Ext3 dando los mismos resultados. El juego ya está actualizado a nivel de parches y demás, no pide CD y funciona bien en Windows. En cuanto a lo del programa, no sé qué programa podría utilizar de ejemplo.. mm, pero de todas formas sé que no tengo instalado DirectX en Wine... lo he intentado pero no me funciona....

---

### Post by chispachips on 2008-05-12
¿Nadie sabe sobre mi problema? :( , estoy probando a ver de todas las maneras que me salen pero no sé... siempre me pasa igual :S

---

### Post by BluePlum on 2008-05-12
O.o why is this in another language?

---

### Post by faktorqm on 2008-05-12
Por que este es el foro de Argentina y acá se habla ESPAÑOL. Igual me encantó tu aporte respondiendo al post original, muy constructivo.

Hay 1500 tutoriales de como instalar WoW en ubuntu, pero la clave es saber cual funciona.... Éste es uno "oficial" [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) no se si ya lo habras visto. Sino creo que tendrias que empezar a buscar las dll's que estan dando problema. Salu2!!

---

### Post by margori on 2008-05-12
> **chispachips said:**
> ... pero de todas formas sé que no tengo instalado DirectX en Wine... 

¿Estas seguro? Yo tengo entendido que viene con ciertas "dll" preinstaladas, o por otro lado, te convendría revisar como se usa directX en Wine. Yo lo estuve buscando por un ratito, pero admito flojera...

---

### Post by chispachips on 2008-05-14
Jaja, tienes razón; la gente dice que viene preinstalado, pero no sé cómo manejarlo ni configurarlo.... por lo menos no me funciona si lo arranco con directx, ni idea..

Jaja, qué chistoso el inglés xDDD

---

### Post by Dreamlocked on 2008-05-14
No hablo español muy bueno.

Pero intenta esto : 

Abre el Config.wtf (.....World of Warcraft/WTF/Config.wtf) y supplementa :
```

SET M2UseShaders "0"

```

y
```
SET pixelShaders "1"
``` o ```
SET pixelShaders "0"
```

---

