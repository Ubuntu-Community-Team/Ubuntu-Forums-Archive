---
title: "Problema al muntar un hd usb extern"
date: 2009-10-25
forum: Catalan Team
---

### Post by Mitsurugi on 2009-10-25
Bones a tothom, últimament, tinc masses problemes amb el HD USB extern, ara mateix, al encendre'l no es munta automàticament, i no m'agrada això, pel que ho haig de fer manualment

```
mitsu@didac-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/disk
```

I a l'hora de desmuntar-lo, doncs el mateix

```
mitsu@didac-desktop:~$ umount /media/disk
```

La meva pregunta es com aconsegueixo que al arrancar el hd, es munti automàticament. Gràcies!

---

### Post by CarlesOriol on 2009-10-25
Comprova a qualsevol finestra del nautilus:

Edita > Preferències > Suport

---

### Post by Mitsurugi on 2009-10-25
[IMG]http://img44.imageshack.us/img44/5984/capturadk.png[/IMG]

---

### Post by CarlesOriol on 2009-10-26
obre un terminal i escriu **sudo dmesg -c** abans de connectar el disc i torna-ho a fer un cop connectat i ens envies el que hi diu. (el segon cop)

---

### Post by Mitsurugi on 2009-10-26
[http://paste.ubuntu.com/302007/](http://paste.ubuntu.com/302007/)

---

### Post by Mitsurugi on 2009-10-30
el pujo...

---

### Post by CarlesOriol on 2009-11-01
Pots fer una prova amb un pendrive? a veure si és problema del sistema o del disc

---

### Post by Mitsurugi on 2009-11-01
I tant, cap problema, et deixo la info al fer mount amb el stick ficat

```
/dev/sdc1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```

Per cert, ara que he actualitzat al 9.10 (reinstalació al damunt formatejant el 9.04 i mantenint el /home/usuari) ja no em serveix el truquillo manual de ....

```

mitsu@mitsu-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/disk
mount: el punt de muntatge /media/disk no existeix

```

---

### Post by Mitsurugi on 2009-11-01
He descobert al karmic això de Utilitat de Discs, sembla que el localitza, però no em deixa muntar-lo des d'allà tampoc

[IMG]http://img509.imageshack.us/img509/2849/utilitatdiscs.png[/IMG]

---

