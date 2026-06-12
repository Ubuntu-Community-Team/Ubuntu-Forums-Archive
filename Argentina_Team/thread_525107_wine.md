---
title: "wine"
date: 2007-08-13
forum: Argentina Team
---

### Post by facundocorradini on 2007-08-13
Hola gentes

Ando necesitando instalar el fireworks8 en wine, pero al tratar  me dice que "no hay espacio suficiente en c:\"

alguien sabe como darle espacio al wine? (aclaro que el rigido "real" tíene varios GB libres)

---

### Post by faktorqm on 2007-08-14
Hola, abri un terminal, escribi "winecfg" (sin comillas).
Te abre una ventana, vas a la ficha UNIDADES, seleccionas la unidad C: y luego presionas el boton EXPLORAR..., entonces ahi por ejemplo le seleccionas la carpeta de una particion con mas espacio. Le das aceptar y ya! Salu2!!

---

### Post by facundocorradini on 2007-08-14
pues resultó ser q en realidad tenía lleno el disco!!! 

es más, en un momento estaba trabajando y salió un globito que decía "tiene el 99% del disco lleno" ....

Esta rara situación me mostró un punto muy fuerte de ubuntu: trabaja muy bien sin importar si tenemos el rígido al 10 o al 99% , y a la vez evidenció un punto débil es bastante dificil saber cuanto espacio libre queda en el rígido...

---

### Post by leo_rockway on 2007-08-15
no es un punto debil saber cuanto espacio libre hay en disco.

para ver cuanto espacio libre hay en el disco en kde podes usar KDiskFree... o algun tema de superkaramba.

en gnome no tengo idea xq nunca use gnome...

por consola podes usar

> df -h

---

### Post by sajnox on 2007-08-15
En gnome tenes el analizador de uso de disco y podes usar algun desklet del Gdesklets, para mi son bastante utiles ademas de que "enchulan el escritorio"

Saludos

---

### Post by facundocorradini on 2007-08-15
Pues bien... por andar tocando cosas sin estar seguro, me he ganado un par de errores:

Ahora cada vez que trato de ejecutar algo con wine, me dice:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.

inclusive cuando trato de entrar a winecfg me dá ese error (aunque se ejecuta)

alguien sabe como puedo solucionarlo?

---

### Post by juanman on 2007-08-16
Debes copiar la carpeta ~/.wine/drive_c a la ubicacion donde hayas puesto en winecfg...

---

### Post by facundocorradini on 2007-08-16
LOL había tratado de poner esa carpeta, pero habia puesto la C con mayúscula...
Creo que voy a tener que empezar a programar un poco menos y dormir un poco más...
------------------------------------

**Muchisimas gracias** gente!!! ahora  puedo usar el fireworks, anda espectacular!! xD

---

### Post by Mataca on 2007-08-16
Además de programar menos y dormir mas, no olvides las mujeres que también liberan la mente :P
:guitar:

---

