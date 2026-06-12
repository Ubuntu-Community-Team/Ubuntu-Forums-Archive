---
title: "configurar particiones windows (nuevo en linux...)"
date: 2007-07-09
forum: Argentina Team
---

### Post by nachito on 2007-07-09
Hola tengo el siguiente problema:

Tengo 2 particiones de windows, la del sistema y una con demas archivos, al iniciar el ubuntu no aparecen montadas, entonces creo 2 puntos de montaje uno en /home/media/Windows y otro en /home/media/Cosas, ahi las monta...

Pero no me deja entrar porque no tengo permisos suficientes, entonces hago en la consola 'sudo nautilus /home/media/Cosas' y 'sudo nautilus /home/media/Windows'.
 
Hasta ahi voy bien pero cuando reinicio la pc tengo q montar y dar permisos todo de vuelta...

Como hago para q sea permanente???

---

### Post by marianom on 2007-07-09
Si no estoy equivocado tenés que ingresar los permisos en /etc/fstab para que te los tome automaticamente cada vez que inicias la máquina.

---

### Post by nachito on 2007-07-09
Bueno agregue este par de lineas al fstab:

/dev/hda1 /media/Windows ntfs ro,user,defaults,auto,umask=1000,nls=utf8 0 0
/dev/hda5 /media/Cosas ntfs ro,user,defaults,auto,umask=1000,nls=utf8 0 0
 
pero solo me monta al inicio la "Windows" la otra no, no se por que :(

---

### Post by nachito on 2007-07-09
Me Equivoque la segunda particion era FAT32 :S ,entonces para la segunda pongo:

/dev/hda5 /media/Cosas vfat gid=100,umask=0007,fmask=0117,utf8 0 0

La monta al incio ahora pero no me da el permiso para navegar!

---

### Post by Al_maverick on 2007-07-09
mi particion fat32 la tengo montada con estas opciones

UUID=10A0-25C9 /media/sda5 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1

---

