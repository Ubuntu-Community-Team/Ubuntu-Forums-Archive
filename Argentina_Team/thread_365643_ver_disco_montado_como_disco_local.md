---
title: "ver disco montado como disco local"
date: 2007-02-19
forum: Argentina Team
---

### Post by zspikes on 2007-02-19
Buenas gente!!!!
la cuestion es la siguiente, hace un tiempo, cuando me inicie en el mundo de ubuntu, monte un disco duro q tengo con guin (puaj) y todos mis archivos. La cosa es q no se como rayos hice q me figuraba como un disco local, me salia en lugares y ademas un acceso directo en el escritorio.

La cosa es q por un problemita reinstale ubuntu y volvi a montar dicho disco duro siguiendo este tutorial [http://gadgetorama.wordpress.com/2006/03/26/como-montar-todas-tus-particiones-en-ubuntu/](http://gadgetorama.wordpress.com/2006/03/26/como-montar-todas-tus-particiones-en-ubuntu/)
pero ahora lo veo como una carpeta dentro de "sistema de archivos"

como puedo hacer para q lo vuelva a ver como otro disco duro?

gracias!!!!!!!

---

### Post by jpmorelli on 2007-02-19
Agregando una línea como la siguiente en /etc/fstab deberías tenerlo como original
Siendo "sda1" =  sd (sata disk o scsi disk ) a ( disco master primario ) 1 (primera partición del disco )
y el directorio /media/sda1 ( o como quieras llamarlo ) tiene que existir

/dev/sda1     /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0  1

luego de editarlo con los parámetros que correspondan

sudo mount -a

---

### Post by zspikes on 2007-02-19
a ver, el disco q yo quiero montar es /dev/hdb1 y la carpeta donde lo monte es /media/datos por lo tanto me deberia quedar algo asi?:
/dev/hdb1 /media/datos ntfs defaults,nls=utf8,umask=007,gid=46 0 1

porq acabo de probar y todavia no lo veo

por las dudas pongo lo q tengo en el fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 /media/datos ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /media/datos ntfs defaults,nls=utf8,umask=007,gid=46 0 1

---

### Post by marianom on 2007-02-19
Vos estás queriendo montar un windows según entiendo de tu post original. 
Seguí las indicaciones de jmorelli pero chequea [este wiki]("https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28windows%29%7C%28mount%29") para acomodar las opciones convenientes a tu disco de windows (esencialmente la ip y ruta de tu otra máquina).

---

### Post by zspikes on 2007-02-19
de nuevo yo, soy medio gil jaja, ahi me di cuenta. tenia q reemplazar la ultima linea, me quedo algo asi

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb1 /media/datos ntfs defaults,nls=utf8,umask=007,gid=46 0 1

reinicie y ya estaba el disco en el escritorio y en lugares, tal cual lo queria :) mil gracias compadre jmorelli!!!

---

### Post by jpmorelli on 2007-02-20
Un placer kpo, y la verdad que hasta cuando leí mi propio post pensé, pobre ni yo entiendo lo que escribí, jajaa, me alegro que vos lo hayas entendido. :KS

---

