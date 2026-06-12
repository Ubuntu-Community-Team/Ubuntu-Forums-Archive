---
title: "no pudo usar una particiones recien hecha"
date: 2007-11-06
forum: Argentina Team
---

### Post by gustmarti on 2007-11-06
Hola gente, resulta que tengo dos particiones en el disco (una para ubuntu una para linux) y estoy queriendo usar el espacio libre para tener una particiòn clasica para datos, musica, fotos, mail, etc, etc. Intenté en ppio hacer una partición primaria ext3 y ext2. Pero cuando quiero guardar cualquier cosa me dice que no tengo los permisos para hacerlo, ya intenté con boton derecho "propiedades", y cambiar los permisos pero no pude.  También intenté sin exito hacer una partición extendida y dentro de esta una lógica, también con resultado negativo. Lo raro es que luego borre las particiones hecha e hice una fat32 que anduvo.
Otro problema es que el editor de particiones desaparece cuando lo estoy usando. 

La cuestión es entonces como puedo crear una particion ext que no me pida los permisos; me convendrìa hacer una usar partición extendida y dentro de esta una lógicala o una fat32? Me conviene usar otro editor de particiones y cual me recomiendan? Saludos!!!!

---

### Post by UBUjuan on 2007-11-07
El problema no es el editor de particiones, sino que después de haber creado una particion tenes que montarla con permisos de escritura. Esto se especifica en el archivo /etc/fstab (ahi vas a encontrar un ejemplo de que opciones poner.

---

### Post by gustmarti on 2007-11-07
todavia no pude. En el archivo que me dijiste aparece esto
[PHP]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=acc2a75b-4111-4fed-bbaf-a56224c8a6f3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=32E00C1EE00BE6C7 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=21BC11E927FACF7E /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=cb8af3e0-98af-4be1-8aa9-784a1622b1a3 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0desconocidodesconocido[/PHP]

en "propiedades " "volumen" tanto en punto de montaje, sistema de archivos y opciones de montaje aparece "not mounted", el tema es que no se donde se debe completar para montar el disco ni tampoco se con que completarlo. Saludos.

---

### Post by Timbis on 2007-11-07
acordate de hacer una copia de todo lo que tienes en el rigido, por si acaso. 
En el Gparted puedes hacer botonderecho y click en 'montar'  
tambien puedes utilizar el gestor de particiones de la instalacion de ubuntu en su liveCD.
Suerte

---

### Post by UBUjuan on 2007-11-08
Lo que vos pasaste es el archivo /etc/fstab , ahi tenes una particion ext3 creada durante la instalacion, si despues creas mas particiones no te van a apacerer automaticamente en este archivo, vos tenes que agregar las particiones manualmente. fijate en [http://orion220.blogcindario.com/2005/09/00025-tutorial-y-manual-de-fstab-para-cualquier-linux-debian-suse-mandrake-mandriva.html](http://orion220.blogcindario.com/2005/09/00025-tutorial-y-manual-de-fstab-para-cualquier-linux-debian-suse-mandrake-mandriva.html)
y en [http://www.yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html)
 para ver como se hace.
Un detalle: averigua sobre algo llamado UUID (podes reemplazar el nombre de una particion /dev/hda1 por ese numero largo, tiene ventajas y desventajas).

---

### Post by gustmarti on 2007-11-08
Bueno gente, esto sigue sin funcionar. Sequí todo los tutoriales recomendados pero sigo sin poder montar la partición. Tampoco pude modificar el fstab porque dice que no tengo permiso o escribi en lugar incorrecto (cosa que creo no haber hecho). Al lado del archivo  fstab hay uno que es  fstab.edgy y otro  fstab.pre-uuid, es lo mismo?
Bue, ya no se que hacer, es bastante mas dificil de lo que pensaba. Espero que algùn iluminado me pueda ayudar así no tengo que reinstalar todo.

---

### Post by Mauro22 on 2007-11-08
Hola,

primero, 

para escribir en el fstab, tenes que abirlo desde la consola con permisos de administrador, sino no te va a dejar

```
sudo gedit /etc/fstab
```


Segundo, 

si en tu pc tenes M$ y Linux, te conviene crear una fat, y montarla con vfat. y listo 0 problemas

Si queres tambien podes hacer una particion NTFS, pero tenes que  instalar el paquete 'ntfs-3g' (con GG ya viene).

---

