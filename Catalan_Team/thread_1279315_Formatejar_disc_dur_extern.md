---
title: "Formatejar disc dur extern"
date: 2009-09-30
forum: Catalan Team
---

### Post by trinkus on 2009-09-30
Hola,

He comprat un disc dur extern de 1Tb de Lacie. Ve amb un soft per windows de manera que si el poses de nou a l'ubuntu nomes té 10Mb lliure (ves!). Al manual nomes parla de Mac i Windows (la resta no existim!) pero l'he obert amb un windows i té una aplicacio de windows per formatejar-lo amb NFTS.
Jo vull formatejar-lo amb ext3 pero la veritat es que no tinc ni idea com es fa... hi ha alguna aplicacio per fer-ho? O alguna comanda de terminal?

Gracies

---

### Post by papapep on 2009-09-30
En entorn gràfic tens el [Gparted]("http://packages.ubuntu.com/jaunty/gparted") (Sistema > Administració > Editor de particions) per a poder modificar, si et cal, les particions i poder-les formatar al que vulguis i, evidentment, l'[fdisk]("http://packages.ubuntu.com/jaunty/gnu-fdisk") per particionar el disc i l'**mkfs** per a crear el sistema de fitxers, aquestes dues al terminal

---

### Post by trinkus on 2009-10-01
Merci Papapep,

Ho he provat amb el Gparted. M'ha costat una mica perque hi havia una particio petita al disc (com de sistema) i no es deixava esborrar. Finalemnt s'ha esborrat i l'he formatada tota. Va bé. Un altre dia ho provo amb fdisk. Gràcies

---

### Post by pauelmaco on 2009-10-03
> **trinkus said:**
> 
Jo vull formatejar-lo amb ext3 


Potser millor que ho facis amb fat32 o Ntfs, perquè així si mai l'has d'endollar a un ordinador amb windows, te'l reconegui, que si li poses amb ext3 només et donará l'opció de formatejar-lo.

---

### Post by papapep on 2009-10-04
> perquè així si mai l'has d'endollar a un ordinador amb windows

Trobo encara millor l'opció de formatar l'ordinador que té el Windows i instal·lar-hi un sistema operatiu lliure, fixa't tu.

---

### Post by pauelmaco on 2009-10-04
> **papapep said:**
> Trobo encara millor l'opció de formatar l'ordinador que té el Windows i instal·lar-hi un sistema operatiu lliure, fixa't tu.

Jo també ho crec així, però potser l'ha d'endollar a l'ordinador "d'algú altre" que no té ni idea de linux.

---

### Post by papapep on 2009-10-04
> Jo també ho crec així, però potser l'ha d'endollar a l'ordinador "d'algú altre" que no té ni idea de linux. 

És clar el perquè ho deies. El que passa és que fer això és perpetuar el domini de sistemes operatius tancats i privatius amb sistemes de fitxers ineficients. Si no hi ha cap previsió real d'haver-lo d'emprar en sistemes no Gnu/Linux, no hi trobo cap motiu per a no formatar-lo a EXT3 o EXT4.

---

