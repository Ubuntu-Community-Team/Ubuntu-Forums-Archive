---
title: "Bootea lento cuando hay otras particiones"
date: 2007-08-28
forum: Argentina Team
---

### Post by zspikes on 2007-08-28
Buenas gente. Tengo un problema con ubuntu... se demora MUCHO en el arranque cuando hay alguna otra particion en el disco.

Lo comprobe porq antes tenia un recovery, y cuando la borre empezo a bootear normal, y ahora q puse debian en otra particion, bootea lento de nuevo.

alguna solucion? gracias!! :D

---

### Post by rretamar on 2007-08-28
Hola.
Supongo que se debe a que ejecuta el fsck cada vez que arranca.  ¿ Es así ?.

Si es eso, podés deshabilitar esa verificación editando el archivo fstab ,fijate en las entradas que correspondan a la partición que no deseas chequear y cambiá los dos últimos números para que ambos estén como ceros.( 0 0)

Por las dudas podés hacerte un respaldo del fstab antes de modificarlo.

Saludetes !

---

