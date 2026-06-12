---
title: "Si hay alguien conectado..ayuda con el grub"
date: 2008-05-15
forum: Argentina Team
---

### Post by ramiro_md on 2008-05-15
Gente estoy complicadisimo, resulta q toque algo de la tabla de partcioones y me quiero re matar xq si bien no guarde los cambios se ve q tuvo su repercusion en el sistema. al iniciar no me carga el grub. Me dice lo siiguiente loading grub...stage 1.5..error 22
si alguiem pme puede ayudar se lo agradceeria..ahora estoy bajo el livecd

---

### Post by divague on 2008-05-15
Tienes que abrir la terminal desde el live cd, y pones:

sudo grub

find /boot/grub/stage1

root (hd?,?)

las ? cambias por el disco que te devuelve el comando anterior, luego:

setup (hd0)

quit

y ya deberia estar re-instalado el grub

---

### Post by faktorqm on 2008-05-16
no te preocupes chabon, eso es por que cambiaste las particiones, entonces el grub tiene mal la informacion fisionomica de tu disco. Reinstalalo como dice aca divague, despues lo configuras a tu gusto :D Salu2!

---

### Post by ramiro_md on 2008-05-17
Muchas gracias gentee..pero tuve q formatear xq no me reconocia ni una sola particion...un saludo, me voy al clasico.

---

### Post by ramiro_md on 2008-05-17
Muchas gracias gentee..pero tuve q formatear xq no me reconocia ni una sola particion...pero lo voy  tener en cuenta para la prox =)un saludo, me voy al clasico =D

---

### Post by ramiro_md on 2008-05-17
Hola amigos, acabo de reinstalar ubuntu, resulta que no puedo acceder a las dos particiones ntfs donde, en una tengo win$ y en otra solo para datos. Yo me acueerdo que la anterior vez habia hecho algo para q me las reconozca pero ya ni se como lo hice, si me podrian dar una mano...desde ya muchas gracias, y ahora si me voy pal clasico =D

---

### Post by Hei Ku on 2008-05-17
Fijate de tener instalado el paquete ntfs-3g. Y despues fijate en el fstab que tengas configuradas esas particiones.
Si tenes dudas o no estan configuradas, pega el /etc/fstab aca y te damos una mano.

---

### Post by sajnox on 2008-05-17
Tambien postea la salida del comando

```
sudo fdisk -l
```

---

### Post by ramiro_md on 2008-05-17
GRacias, pero las reconocio solo, re raro jejeje...un salduo...


"...no tenes verguenza hasta el grana dio la vueltaaa..."

---

### Post by faktorqm on 2008-05-18
<OT> estudian!!! estudian!!!! estudian!!!

esto se lo dedicamos con todo nuestro cariño a chipknot :KS

yo tengo un hijo bobo, 
se llama lobo,
que voy a hacer....
quizo salir primero, 
pero no pudo,
se fue a la B....
</OT>

Como puede ser que te lo reconocio "solo"?!? instalaste el ntfs-3g? o sea, el kernel tiene soporte para ntfs pero es limitado. 
Comentalo asi si alguien tiene el mismo problema lo puede solcionar. Gracias! Salu2!!!

---

### Post by ramiro_md on 2008-05-19
faktorqm la verdad no me acordaba de haberlo instalado, pero me fije en el gestor de paquetes y se ve que si lo hice porque figura instalado el "ntfs-3g"..asique si a alguien ubuntu no les reconoce las particiones ntfs instale el "ntfs-3g" desde el gestor de paquetes synaptic.











GIlnasia y lagrima de la plata...todo lo que NO quiero ser.

---

