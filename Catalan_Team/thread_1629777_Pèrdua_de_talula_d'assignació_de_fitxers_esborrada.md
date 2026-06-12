---
title: "Pèrdua de talula d'assignació de fitxers esborrada a l'intentar formatar un altre dis"
date: 2010-11-24
forum: Catalan Team
---

### Post by marteljorge on 2010-11-24
Tenia connectades dos memòries sólides USB a un Ubuntu-desktop 10.04. Vaig emprar el "creador de discos d'arrencada" per "esborrar" /dev/sdb1, es van desmuntar els dos dispositius, /dev/sdb1 es va quedar sense informació i /dev/sdc1 es va quedar completament inútil.
Edito:
La taula d'assignació es va anar a pastar fang, no es va esborrar, però es va fer malbé. Algú sap com podria fer per recuperar-ho?
Se m'acut que podria bolcar el dispositiu a un fitxer i llevar-li la taula de particions, però no conec com fer-ho.

---

### Post by wgarcia on 2010-11-26
No queda clar si demanes ajuda per intentar recuperar alguna informació d'aquests discos o simplement comentes el que ha passat.

---

### Post by marteljorge on 2010-12-09
Les dos cosses. Alguna idea?

---

### Post by wgarcia on 2010-12-10
En quant a per què ha passat, és difícil esbrinar-ho, però possiblement s'ha intentat crear alguna partició i el procés es va truncar en algun moment i va quedar a mitges. 

En quant a com recuperar-ho, el primer que es podria provar és veure si el programa "parted" pot veure la partició o particions que hi havia i recuperar la taula de particions. El primer és assegurar-se que el disc no està muntat, i si és per exemple /dev/sdb, des de la línia de comandes fer:

umount /dev/sdb

Després donar la instrucció:

sudo parted /dev/sdb

perquè faci servir el disc en qÜestió. I per últim:

rescue START END 

a veure si recupera les particions del disc. 

Si això fallés es podrien seguir les instruccions dels post següent:


[http://ubuntuforums.org/showthread.php?t=1471031](http://ubuntuforums.org/showthread.php?t=1471031)


per veure de recuperar dades dels discs si hi tenies coses importants.

---

### Post by marteljorge on 2010-12-10
> **wgarcia said:**
> En quant a per què ha passat, és difícil esbrinar-ho, però possiblement s'ha intentat crear alguna partició i el procés es va truncar en algun moment i va quedar a mitges. 

En quant a com recuperar-ho, el primer que es podria provar és veure si el programa "parted" pot veure la partició o particions que hi havia i recuperar la taula de particions. El primer és assegurar-se que el disc no està muntat, i si és per exemple /dev/sdb, des de la línia de comandes fer:

umount /dev/sdb

Després donar la instrucció:

sudo parted /dev/sdb

perquè faci servir el disc en qÜestió. I per últim:

rescue START END 

a veure si recupera les particions del disc. 

Si això fallés es podrien seguir les instruccions dels post següent:


[http://ubuntuforums.org/showthread.php?t=1471031](http://ubuntuforums.org/showthread.php?t=1471031)


per veure de recuperar dades dels discs si hi tenies coses importants.

La taula de particions és correcta. Falla la FAT. Encara més, l'espai està assignat a fitxers que no deurien existir amb noms (aparentment) una mica aleatoris.

---

### Post by wgarcia on 2010-12-10
Pots provar doncs amb testdisk, és un programa que pot veure les particions que hi havia al disc, tot i que el FAT estigui danyat, i proposar-te recuperar l'estructura d'aquestes particions:

sudo apt-get install testdisk 

Des d'una terminal 

sudo testdisk

t'obre una pantalla que és força auto-explicativa.

---

### Post by marteljorge on 2010-12-11
Tot i això, amb el testdisk no ho aconsegueixo "desborrar" perquè els sectors estan assignats a fitxers "pseudo-aleatoris". (Com esborrar la taula per crear-ne una de nova sense esborrar els sectors de les dades?)

---

### Post by wgarcia on 2010-12-12
Quin sistema de fitxers tenen els discs en qüestió? Vfat?

---

### Post by marteljorge on 2010-12-13
> **wgarcia said:**
> Quin sistema de fitxers tenen els discs en qüestió? Vfat?

Pensava que, parlant de taula d'assignació, era evident que és vfat.

---

### Post by wgarcia on 2010-12-14
Sí, perdona, potser sí que era evident. Una possibilitat seria fer un "fsck.vfat" o un "chkdsk" des d'un CD de recuperació de Windows, però no sé si aquestes utilitats poden reparar una taula d'assignació de fitxers danyada. Si ho vols provar des d'ubuntu, hauries de desmuntar primer el disc en qüestió (sudo umount /dev/s...) i després donar la instrucció "sudo fsck.vfat /dev/s..." (tot i que em sembla que si poses "fsck" directament ja crida a "fsck.vfat" si es tracta d'un sistema vfat).

---

### Post by marteljorge on 2010-12-19
> **wgarcia said:**
> Sí, perdona, potser sí que era evident. Una possibilitat seria fer un "fsck.vfat" o un "chkdsk" des d'un CD de recuperació de Windows, però no sé si aquestes utilitats poden reparar una taula d'assignació de fitxers danyada. Si ho vols provar des d'ubuntu, hauries de desmuntar primer el disc en qüestió (sudo umount /dev/s...) i després donar la instrucció "sudo fsck.vfat /dev/s..." (tot i que em sembla que si poses "fsck" directament ja crida a "fsck.vfat" si es tracta d'un sistema vfat).

El problema radica en que les dos còpies de la taula s'han anat a pastar fang, així que l'fsck em diu que és correcte.
No se m'acut què més fer...

---

