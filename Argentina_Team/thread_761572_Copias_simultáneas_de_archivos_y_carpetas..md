---
title: "Copias simultáneas de archivos y carpetas."
date: 2008-04-21
forum: Argentina Team
---

### Post by ramiro_md on 2008-04-21
Hola ubunteros, hace rato que no posteaba, y ayer a la noche me surgió una duda y quería saber si me podrían ayudar.
El tema es el siguiente en esta computadora yo trabajo tanto con win xp como con ubuntu. En la partición de ubuntu tengo mi carpeta de archivos personales "ramiro" y en la partición de windows también tengo una carpeta de similares características. Lo que me gustaría hacer, si se puede, es tener actualizadas las dos carpetas constantemente...es decir si yo modifico una archivo en la carpeta de la partición Linux que se modifique en simultaneo ese mismo archivo alojado en la partición de windows. Y viceversa, aunque esto ultimo no lo creo posible ya que win no lee las particiones ext3 :(
Bueno, desde ya muchas gracias.

---

### Post by tzulberti on 2008-04-21
Windows lee EXT3 si le instalas un driver especial que hay para eso:
[http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/](http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/)

Fuera de eso, creo que nada mas necesitarias un programa de sincronizacion, pero nunca use alguno asique no te puedo recomendar.

---

### Post by Thalskarth on 2008-04-21
> **tzulberti said:**
> Windows lee EXT3 si le instalas un driver especial que hay para eso:
[http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/](http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/)

Fuera de eso, creo que nada mas necesitarias un programa de sincronizacion, pero nunca use alguno asique no te puedo recomendar.

Creo que lo mas sencillo, seria que usando un driver como el que te recomienda tzuberti,

Seria hacer que ambos usen la misma carpeta del mismo disco. Entonces, al tener los 2 accseso a ella, te evitas lo de sincronizar y lo de gastar mas espacio al tener todo 2 veces en 2 carpeta

---

### Post by ramiro_md on 2008-04-21
si, muchas gracias, eso tenia pensado hacer...dejare solo una partición ntfs para datos y ahí alojare mi carpeta "compartida".
Muchas gracias...

Otra consulta...como saco el pass en el inicio de sesión ???

---

### Post by margori on 2008-04-21
> **ramiro_md said:**
> como saco el pass en el inicio de sesión ???

Te recomiendo no sacarle el password a tu usuario. Sería una disminución extrema de la seguridad de tu computadora.

Hay una posibilidad haciendo que Ubuntu inicie sesión en un usuario predeterminado. Lo pones en Sistema -> Administración -> Ventana de entrada -> Seguridad -> Activar entrada automática.

---

### Post by uidb4056 on 2008-04-21
Hay un programa para sincronizar carpetas en el repositorio de Ubuntu que se llama **unison**, creo que te podria servir ejecutadolo desde Ubuntu teniendo montada la partición de windows.

---

### Post by faktorqm on 2008-04-22
Linux lee ntfs a través del paquete ntfs-3g
Windows lee ext3 a través de un driver ext3. Aca tb tenes otra dire: [http://www.fs-driver.org/](http://www.fs-driver.org/)
Dicho esto no veo necesidad alguna de sincronizar nada, teniendo identico acceso a la carpeta desde los dos SO al mismo tiempo. Salu2!!

---

