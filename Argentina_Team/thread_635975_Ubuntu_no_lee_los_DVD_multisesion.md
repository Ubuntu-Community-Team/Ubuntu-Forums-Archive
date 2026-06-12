---
title: "Ubuntu no lee los DVD multisesion"
date: 2007-12-09
forum: Argentina Team
---

### Post by ideafix on 2007-12-09
Hola gente. El problema es simple como el titulo.  Cuando pongo en la lectora de DVD un dvd que tiene dos sesiones, parece q lo va a leer pero se queda ahi. Pongo alguno q haya grabado de una, y enseguida me aparece el acceso directo en el escritorio y todo ok. Como puedo solucionarlo? En Wind.... todos se leen, y descarten de plano problema de la lectora o de los dvd, el problema es el mismo con dvds de distinta marca. Ah, los dvd estan grabado en nero como dvd de datos, por si sirve, y estoy usando Ubuntu 7.04. Desde ya gracias!!!!

---

### Post by Hei Ku on 2007-12-09
tenes instalados todos los codecs para dvd?

---

### Post by ideafix on 2007-12-09
codecs para dvd? :shock: esos no los conocia. Para la grabadora de dvd decis? Por lo q estuve leytendo pense q estaba mas orientado a un tema de configuracion. Les pongo los q dice el /etc/fstab, ya q lo lei en otro foro:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=f8ac0e0e-c455-4865-8c90-edb0e8f5a885 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=5AE4DF76E4DF533D /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=782C62AF2C626858 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=098365a6-5137-42bb-bc5a-ce0ea9315e02 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   auto    user,noauto     0       0
/dev/hdb        /media/cdrom1   auto    user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

le modifiq en las lineas q dicen cdrom en la columna type puse auto, tal comoo lei, pero sigue pasando lo mismo (en lugar de auto decia iso9660,udf ).

---

### Post by ideafix on 2007-12-17
nada?[-o<

---

### Post by faktorqm on 2007-12-18
Lo que a mi no me cierra es que tiene que ver los codecs con un dvd multisesion? una cosa es la forma en que codifican los datos para leer/escribir y la otra es la forma en la que se escriben los datos fisicamente al disco.
Estas seguro que el problema es que no te lee discos multisesion? o es que pones un cd y no te lo monta? Describi mejor tu problema por favor, agregando modelo de pc, version de *buntu, 32 o 64, modelo lectora/grabadora, etc
salu2!!

---

### Post by marianom on 2007-12-19
En kb3 tenes que tener unas librerias extras instaladas para que pueda trabajar con multisession, capaz que para el programa que estés usando también faltan (ya se que no aporté mucho pero con intentar nada se pierde).
Ahora me caigo del sueño pero mañana hago una busqueda rápida a ver si encuentro algo más.

---

### Post by faktorqm on 2007-12-19
mira esto por las dudas capaz ter ayuda

[http://ubuntuforums.org/showthread.php?t=643854](http://ubuntuforums.org/showthread.php?t=643854)

---

