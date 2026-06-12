---
title: "MicroSD 4GB morta?"
date: 2011-08-26
forum: Catalan Team
---

### Post by Joan Marc on 2011-08-26
Hola!
Doncs tinc una targeta MicroSD que ni el Windows ni l'Ubuntu me la detecten, i em preguntava si hi ha alguna cosa a fer per poder recuperar-la. Des del terminal que fet un lsusb en el que no m'ha semblat veure res en referència a la targeta, i també un fdisk -l però m'ha sortit una parrafada immensa que no entenc ni un esborrall...
Algun suggeriment?
Gràcies!

---

### Post by wgarcia on 2011-08-29
Pots endollar la targeta i des d'una terminal fer:

dmesg

i mirar les últimes línies del que surt, a veure si reporta algun error en intentar llegir la targeta, però tot pinta que s'ha fotut. Una altra cosa que es pot intentar és reformatejar-la.

---

### Post by Joan Marc on 2011-08-29
Em detecta el lector, però no la targeta:
```
[  586.505732] scsi8 : usb-storage 2-2:1.0
[  587.505077] scsi 8:0:0:0: Direct-Access     Generic  Card-Reader      1.05 PQ: 0 ANSI: 2
[  587.506690] sd 8:0:0:0: Attached scsi generic sg2 type 0
```

Com puc reformatejar-la si no me la detecta?
Moltes gràcies!

---

### Post by wgarcia on 2011-08-29
Tens raó, si no la detecta no es podrà formatejar.

Pel que es veu amb "dmesg" no munta el dispositiu, tot pinta a què la targeta ja no funciona.

---

### Post by Joan Marc on 2011-08-29
El més probable és que estigui morta ja que no hi ha cap lector (ho he provat amb 5 diferents) ni amb cap ordinador (4 diferents) ni cap mòbil (3 diferents) ni amb res em funciona.
Moltes gràcies igualment!

---

