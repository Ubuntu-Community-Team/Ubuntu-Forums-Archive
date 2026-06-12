---
title: "Muntar unitat automàticament"
date: 2012-11-21
forum: Catalan Team
---

### Post by karto_on on 2012-11-21
Hola a tots, 

tinc la partició d'ubuntu i la del win i vull que quan obri l'ubuntu, la unitat de win es munti automàticament, però no me'n surto.
Faig servir el MountManager, però cada vegada que reinicio el sitema, em surt un missatge que diu algo així com que si vull muntar la unitat manualment apreti M i si la vull muntar més tard apreti S.
I és un rotllo, pq he d'anar al MountManager cada vegada...
No hi ha cap opció de fer-ho automàtic?

Moltes gràcies!

---

### Post by CarlesOriol on 2012-11-23
copia l'arxiu /etc/fstab per que el veiem.

O els paràmetres estan malament o bé la unitat té errors (si es aquest cas comprova-ho fent un xequeig de disk del windows.

---

### Post by karto_on on 2012-11-29
Hola CarlesOriol, 

proc            /proc           proc    defaults        0       0
UUID=b1fce8a9-6b0f-4f9a-b93f-3cc55a430478 /               ext3    relatime,errors=remount-ro,user_xattr 0       1
UUID=5b381738-ae44-4aad-b56a-d06b976f4229 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hda1  /media/windows  ntfs  auto,ro,exec,users,dmask=000,fmask=111,nls=utf8  0       0
/dev/hda1       /media/windows    vfat    gid=100,umask=0007,fmask=0117,utf8 0       0

està tot bé?

Salutacions,

---

### Post by karto_on on 2012-12-01
ok, ja ho he trobat.

[http://onoametal.wordpress.com/2011/07/19/montar-particiones-ntfs-automaticamente-en-ubuntu-11-04/](http://onoametal.wordpress.com/2011/07/19/montar-particiones-ntfs-automaticamente-en-ubuntu-11-04/)

salut a tothom!

---

