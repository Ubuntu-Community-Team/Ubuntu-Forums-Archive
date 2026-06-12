---
title: "Passar Grub de USB al Ordinador"
date: 2012-05-10
forum: Catalan Team
---

### Post by cabanesmusic on 2012-05-10
Em vaig equivocar instalant el Ubuntu 12.04, i ho vaig fer amb arranc grub per usb, i com tinc altres sistemes operatius estic obligat a arrancar--ho tot amb el usb, voldria intentar que el grub estigui en l'ordinador i no en el usb. Què tinc que fer?

---

### Post by wgarcia on 2012-05-12
Pots instal·lar el grub al Registre Mestre d'Arrencada (MBR, Master Boot Record) del disc que vols obrint una terminal in entrant a ella:

```
sudo grub-install /dev/XXX
```

on "/dev/XXX" és el codi de dispositiu del disc on el vols instal·lar. El pots determinar fent:

```
sudo fdisk -l
```

Aquí podràs veure els codis del disc, sols has de fer servir el codi general del dispositiu, no de la partició, és a dir en el meu cas per exemple és "/dev/sda".

---

### Post by pablinsfc on 2012-05-23
Bona tarda,

a mi m'ha passat exactament el mateix, però he seguit la instal·lació automàtica de l'ubuntu formatejant el disc i instal·lant de nou.

A l'acabar la instal·lació el sistema no arrancava si no tenia el pendrive connectat (la instal·lacio es va fer via USB ja que el portàtil no té CD).

Instal·lant el grub al disc dur com es comenta a aquest fil ha quedat resolt, però voldria afegir una reflexió: pot ser que per defecte la instal·lació via USB instali el grub al pendrive en comptes del disc dur? Perquè llavors molta gent s'hi trobarà...

Gràcies per tot!

Pau.

---

### Post by wgarcia on 2012-05-24
Ara no ho recordo perfectament, però em sembla que el normal és que la instal·lació via USB instal·li el GRUB al MBR del disc dur de l'ordinador, alguna opció s'ha d'escollir malament durant el procés d'instal·lació perquè acabi al disc extern. 

Ara bé, potser sí s'hauria de repassar les opcions que dóna l'instal·lador a veure si són prou clares i on es produeix el malentès que acaba amb el GRUB instal·lat on no toca.

---

