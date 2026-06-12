---
title: "Particiones a Solo Lectura de manera aleatoria"
date: 2008-02-28
forum: Argentina Team
---

### Post by godzeus on 2008-02-28
Es problema o inconveniente es que muy de vez en cuando una particion que uso para descargas se vuelve a Read-Only sola, y lo unico que puedo hacer para ponerla normal es reiniciando.
Alguien tiene idea de porque es que sucede esto?

Saludos

---

### Post by User21 on 2008-02-29
Usas 7.04 o 7.10?
La partición es FAT32, NTFS o EXT3 ?
Tenés Inicio Dual con Windows XP o Vista ?
Siempre con el mismo usuario? o al cambiar de usuario ?
Cerrás apropiadamente Win al salir ? 

Con un poco mas de info, te podemos ayudar.

---

### Post by godzeus on 2008-02-29
> **User21 said:**
> Usas 7.04 o 7.10?
La partición es FAT32, NTFS o EXT3 ?
Tenés Inicio Dual con Windows XP o Vista ?
Siempre con el mismo usuario? o al cambiar de usuario ?
Cerrás apropiadamente Win al salir ? 

Con un poco mas de info, te podemos ayudar.
ok, gracias por el interes
Ubuntu Fesity Fawn 7.04 ( a la espera de Hardy)
1) Ext3
2) No tengo Windows ( jejejeje)
3) Siempre con el mismo usuario
4) Goto 2 ( es broma)
es algo muy raro, por lo poco que pude averiguar a ningun amigo mio le paso.
Si tenes alguna idea te lo agradeceria mucho.

Saludos

---

### Post by newtonfn on 2008-03-01
El motivo más normal para que una partición se cambie a modo de solo lectura es que durante alguna lectura/escritura en el disco, el sistema operativo haya detectado un error en el.

Te aconsejo, cuando este en modo de solo lectura y aun mejor, desmontada (hacerlo con una particion escribible y montada es suicidio te lo digo por experiencia) que le hasgas un fsck para ver si no hay anomalías.

A mi me sucedía cuando un disco rígido mio estaba en las últimas. Tenía sectores defectuosos y no habia había format que lo salvara. Cambiamos de disco y santo remedio.

Por tal motivo, cuando le pases un fsck hacelo con el parámetro -c para que chequee los sectores dañados.

Otra cosa que podes hacer, antes de todo esto es simplemente mirar los logs del sistema, para ver si hay algun warning o error o algo que te idique por que motivo el disco se fue a readonly (te diría que archivos es el que debería indicarte esto, pero no lo recuerdo realmente.. fijate en syslog, dmesg por lo menos)

Una ultima cosa ! Para montarlo en lectura escritura, si no es el root, basta con que lo desmontes y lo montes nuevamente.. si tenes la desgracia que justo es el disco en donde tenes el root del filesystem (o esta siendo usado) hay solución, se puede volver a montar un disco en forma de rw, pero es otra de las cosas que no recuerdo, aunque seguor en google está la solución

Espero te sirva
Saludos

---

### Post by sajnox on 2008-03-01
Si queres revisar un disco sin montarlo la mejor opcion es desde un live cd

---

