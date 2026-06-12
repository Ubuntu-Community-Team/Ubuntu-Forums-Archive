---
title: "Problema al descomprimir archivos con &quot;ñ&quot;"
date: 2007-04-27
forum: Argentina Team
---

### Post by matog on 2007-04-27
Hola gente. Tengo una carperta comprimida que en el nombre tiene la letra "ñ". Lo abro con el fileroller y donde está la Ñ me aparece un simbolito raro. Y cuando lo descomprime, hace desastres....

Como lo puedo solucionar?
Gracias!

---

### Post by Al_maverick on 2007-04-27
Que formato de compresion es? 
Probaste de descomprimirlo por linea de comando? 
Exactamente que hace? corrompe el contenido, mezcla los nombres de archivos?

Probaste de descomprimirlo sin la estructura de carpetas? (descomprimir todos los archivos a un solo lugar sin tener en cuenta la estructura de carpetas que tiene el archivo comprimido)

---

### Post by spg76 on 2007-04-27
Es un prioblema de codificación del idioma. 
Yo tenía un problema similar cuando quería descomprimir algo con un caracter "extraño" en una partiión NTFS (nunca tuve problemas con ext3)
Creo que lo arreglas editando el archivo fstab, aunque nunca me preocupe demasiado para hacerlo.
No sé si será tu caso, pero mi solución era descomprimir los archivos problematicos en la partición de Linux aunque esto no es una solución muy definitiva.

---

### Post by kowal on 2007-04-27
Posteá tu archivo /etc/fstab a ver si es un tema de condificación de la partición.

---

### Post by beuno on 2007-04-27
Con renombrarlo tambien lo solucionas  :D

---

### Post by Al_maverick on 2007-04-27
> **beuno said:**
> Con renombrarlo tambien lo solucionas  :D

:D :D

Salvo que el nombre con ñ sea de los que esta dentro del archivo. Yo tuve problemas similares descomprimiendo en una particion FAT32. Ahora descomprimo todo en la ext3 y despues lo copio a la FAT32 si es necesario.

---

### Post by matog on 2007-04-30
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3b2adacc-cbbe-45be-a11e-1e50a8bbb91a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=54D8F7CCD8F7AA7E /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=44CB-A12C  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=57f7bb6e-fb05-49ec-8a60-e0a0d6605c66 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Renombrando los archivos dentro del RAR no me soluciona nada...
Pero voy a hacer un intento en WINDOWS para ver que ****** trae el archivo y poder comparar...

---

### Post by Al_maverick on 2007-05-01
Si tenes una particion ext3, descomprimirlos ahi no deberia traerte problemas. Si no, pone exactamente los errores que te da.

---

