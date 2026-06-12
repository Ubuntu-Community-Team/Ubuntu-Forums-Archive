---
title: "¿Modificar el fstab?"
date: 2007-03-17
forum: Argentina Team
---

### Post by Federick on 2007-03-17
Hola!

Desde hace tiempo los vengo siguiendo como testigo mudo, y ahora se me presentó un problema que no puedo resolver.

Resulta que, aburrido de la falta de problemas del Edgy, me pasé al Feisty Fawn.
Lo complicado fue realizar las particiones desde el live cd y hacer andar el famoso speedtouch 330 de Speedy.
Pero eso ya fue hecho.

Ahora tenemos el problema, que me había sucedido también con el edgy, pero lo resolví con una reinstalación.

La única forma de acceder a las otras particiones de mi disco es a través de la carpeta /media . No tengo acceso directo ni en el escritorio ni desde Computer.

Mi rígido es un SATA de 80GB, y el fstab es éste:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=8f05a389-512d-484b-82a2-2e6b6fa89a49 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=70788F0C788ECFF0 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=45B4-326E  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=4e26f7c1-9179-4dcc-938b-23e62e1bfafc none            swap    sw              0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Mi nivel de linux no es alto.

Bueno, un saludo a la comunidad, y desde ya, gracias.

Fede.

---

### Post by Federick on 2007-03-17
¿Resuelto o me mandé una?

Eliminé la palabra default de sda1 y sda5 en el fstab.

Ya tengo los iconitos :)

Me basé en [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Confirmen por favor si es válido este método, ya que hay varios usuarios con este problema.

Saludetes.


EDIT: Ya encontré un problema, no puedo desmontar estos drives.

---

### Post by felipelerena on 2007-03-18
para, no entiendo nada. cual es el problema? te respondiste solo a tu pregunta? Dios...

---

### Post by Federick on 2007-03-18
> **felipelerena said:**
> para, no entiendo nada. cual es el problema? te respondiste solo a tu pregunta? Dios...
Ja, ja, ja...
El problema era que en el escritorio no tenía los accesos directos a las otras particiones.
Parece ser que es un error de la instalación.
Ahora mi duda es si con el cambio que hice no me mandé una macana. Por ahora parece que no, excepto quizá con el tema de que como usuario común no puedo desmontar las particiones (¿es importante ésto?).

Bueno, gracias por responder felipelerena.

Saludos.

---

### Post by strugart on 2007-03-18
En el escritorio solo aprece uidades montables esto es flash usb, cds dvds etc...
Si blockeaste el mount del disco nunca vas a poder sacar el disco osea desmontarlo (nada grave claro a menos que le disco muera o algo de ese estilo). Espero haber ayudado. Strugart.

PD: Con la nueva version de ubuntu trata de no hacerlo de nuevo el enlace no es necesario, va para mi.

---

### Post by DuckMan on 2007-03-18
mira, a mi me pasa lo mismo y es un bajon, y recuerdo q me paso siempre cuando instalaba un nuevo upgrade de ubuntu...

tendria q probar lo de sacar el default pero no se, eso de q solo aparecen los iconos de los removibles es medio chamuyo strugart, yo pude hacer aparecer el de una particion ydespues no se porq desaparecio. Y eso de q no es necesario, a mi no me parece asi, es un bajon tener q ir hasta media para acceder a algo tan facil

---

### Post by felipelerena on 2007-03-18
y si no aparecen crea un enlace simbolico y listo....

---

### Post by DuckMan on 2007-03-18
pero tampoco aparece en lugares, y la idea no es parchear.. si esta hecho seria bueno q ande

igual no les pido una solucion (??) pero bueno, todavia hay cosas q pulir

---

