---
title: "Montar particion automaticamente"
date: 2007-05-27
forum: Argentina Team
---

### Post by seba2611 on 2007-05-27
Bueno lo que quiero hacer es que me monte mi particion EXT3 q tengo para datos de forma automatica y con permisos de escritura, la cree con el gparted pero solo me la monta com permisos de lectura , como puedo hacer para q lo hago de la otra manera como yo quiero?? intente cambiando los permisos pero no me dejo y como soy nuevo no me animo mucho a tocar el fstab por que no es como el del dapper a simple vista..esto es lo que me da el fdisk - l :

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2846    22860463+   7  HPFS/NTFS
/dev/sda2            2847        5278    19535040   83  Linux
/dev/sda3            5279        9729    35752657+   f  W95 Ext'd (LBA)
/dev/sda5            6495        6618      995998+  82  Linux swap / Solaris
/dev/sda6            5279        6494     9767457   83  Linux
/dev/sda7            6619        9729    24989076   83  Linux

la sda7 es la particion que quiero montar.

Muchas gracias por la ayuda!!!

---

### Post by undiaperfecto on 2007-05-27
yo cuando me paso, hice sudo nautilus en terminal, y ahi le cambie los permisos dandole boton derecho, propiedades, permisos.

---

### Post by seba2611 on 2007-05-28
Listo pongo como losolucionepor si alguien le pasa lo mismo , agregue en el fstab la particion con el punto de montaje asi:

/dev/sda7    /media/datos ext3 rw,user,auto 0 0

y luego le cambie a la carpeta lost & found los permisos a mano y listo quedo perfecto.

---

### Post by Shot on 2007-05-28
--Nada ya lo resolvi--

---

