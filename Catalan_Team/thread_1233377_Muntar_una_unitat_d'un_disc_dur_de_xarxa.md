---
title: "Muntar una unitat d'un disc dur de xarxa"
date: 2009-08-06
forum: Catalan Team
---

### Post by xoldy on 2009-08-06
Hola a tots, bona nit.
voldria que em donéssiu un cop de ma amb el muntatge d'unitats smb a l'inici.
us faig cinc cèntims. Vaig comprar un disc dur ethernet que he connectat al router wifi, i veig la unitat via ip pel nautilus sense cap problema.

ara voldria si és possible poder disposar del disc muntat com si fos un recurs més de xarxa que hauria de tenir disponible en cada inici de sessió.

googlejant he trobat una comanda que m'ha funcionat, i que em munta la unitat correctament.

```
mount -t smbfs -o username=admin,password=catalonia,chmod=777 //192.168.1.106/copies/Home /media/copia
```

l'he de fer manual, i voldria aprendre com fer que sigui automàtica. S'ha d'afegir al fstab? de quina manera?

Com sempre, moltes gràcies a tots!
Jordi

---

### Post by PatrickVogeli on 2009-08-06
prova aixo possant-hi aixo i reinicia, a veure si funciona
```
//192.168.1.106/copies/Home /media/copia smbfs username=admin,password=catalonia,chmod=777 0 0
```

---

### Post by pauelmaco on 2009-08-07
Prova de posar aquesta comanda a: Sistema - Preferències - Aplicacions d'Inici.

---

### Post by xoldy on 2009-08-08
Hola a tots, i moltes gràcies Patrick i Pau per les vostres ràpides respostes. Ara he provat la solució Pau, però no ha passat res, ja que la xarxa wifi costa d'agafar. Imagino que els programes d'inici, arrenquen un pelet abans que no es connecti la wifi (tot i que va molt ràpida la connexió a wifi comparat amb altres sistemes privatius dels que costa treure's la síndrome d'Estocolm).

he creat un arxiu .sh amb permisos 755, i un cop tot és en marxa, l'executo amb un:
```
sudo ./munta_discs.sh
```

em queda per provar la solució Patrick, que imagino que l'he de posar a l'fstab, oi?
actualment a l'fstab tinc;
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b3346645-7637-4c9c-8664-c64aeab71409 /               ext3    relatime,erro$
# /dev/sda3
UUID=8652577c-2456-4a4c-8254-67eb363de8ef /home           ext3    relatime     $
# /dev/sda2
UUID=e697bf12-eae8-4077-80d7-c8198188a735 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

no ho he provat perquè encara temo el tema UUID. Que vol dir? Que he de posar?

Un altre cop, gràcies per dedicar-me el vostre temps.

Jordi

---

### Post by PatrickVogeli on 2009-08-08
posa el que t'he posat tal qual, al final de l'fstab, guarda i reinicia.

Si funciona, be, si no, ho tornes a borrar i ja esta.

salut

---

### Post by xoldy on 2009-08-17
Tremenda l'ajuda! moltes gràcies, la veritat es que m'ha muntat les unitats que volia de la manera que m'has indicat Patrick. Cada vegada estic més enganxat al nostre sistema operatiu! La pega que li he trobat a la solució d'en Pau es que no munta les unitats un cop s'ha connectat a la xarxa.

Com sempre moltes gràcies pel vostre temps! a tots!

Salut
Xoldy

---

