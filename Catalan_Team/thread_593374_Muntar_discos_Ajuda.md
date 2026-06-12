---
title: "Muntar discos: Ajuda"
date: 2007-10-27
forum: Catalan Team
---

### Post by Skaw on 2007-10-27
Hola, aquest és el meu primer missatge ací ja que fa 2 dies que vaig provar l'Ubuntu (7.10)

Bé, després de molt de temps, vaig decidir-me a instal·lar-me la darrera versió del Ubuntu, però no ha parat de donar-me problemes (probablement per la meua nul·la idea de cap SO que no siga Windows).

Bé, jo tinc 2 discos durs, una unitat de 230 GB en NTFS on tinc instal·lat windows xp, i altre de 120 GB en FAT32 on tenia dades, música, etc i molt espai buid, aixì que ahi vaig instal·lar-ho. No recorde ben bé quina opció vaig agafar a la hora d'instal·lar l'Ubuntu (crec que "utilitzar tot el disc") però em va crear una partició dins del disc dur que volia fer servir, i no em carrega el disc dur de 230 GB on tinc informació que necessite (De fet, m'haurà fotut el sistema d'arrancament ja que no em reconeix que tinc Windows quan inicie el PC, i he de tirar d'un CD de BOOT per a entrar-hi) i tampoc em carrega la resta de partició del disc dur.

Entrant a Windows puc accedir a tot el disc dur (el de 230) pero del altre no puc tocar ni la partició amb Ubuntu ni la partició que no ha estat tocada (de fet, no m'ix al Mi PC) i m'agradaria recuperar-les.

Les meues preguntes son:

A) Com puc muntar la partició del mateix disc i el disc dur amb Windows?
B) Com puc reparar el sistema d'arrancament per a que em reconega els SO que tinc instal·lats als dos discos durs?

Vos deixe una imatge per a fer-vos cinc centims
[IMG]http://img132.imageshack.us/img132/9756/discosuo3.jpg[/IMG]

---

### Post by jerec on 2007-10-27
Amb el Windows no podras veure les dades del disc dur de linux.
El Windows no te ni la mes remota idea d'arribar a saber que es un sistema de fitxers EXT3 o una particio Swap
Ja no parlen d'arribar a saber res de permisos, journaling, etc,etc,

El windows veu dues particions a un segon disc dur pero no enten amb que estan fetes, perque nomes coneix Fat32 i NTFS, es per aixo que no els hi assigna lleta d'unitat.

Pero, perque vols veure les dades de Linux al Windows?¿

---

### Post by Skaw on 2007-10-27
No és ben bé això. Si no que vull traure dades del disc dur, on està la partició amb Ubuntu. És a dir, tinc un disc dur amb 2 particions, una on tinc dades de Windows i altre amb l'Ubuntu. 

El que vull fer és, des de Windows (O l'Ubuntu, si em reconeguera el disc dur on tinc Windows), per a passar les dades d'una partició de windows a el disc dur amb Windows.

O per lo menys, que em reconega el disc dur i l'altra partició l'Ubuntu

---

### Post by jerec on 2007-10-27
Dons desde Linux:

com a root:
1º # fdisk -l (aixo et dira les particions que tens, segurament  "sda1" deu esser la particio de Windows, sda 2 la swap i sda3 l'arrel /).

2º La poses al fstab, que es troba a /etc/fstab, l'edites i afegeixes aquesta linea.
Suposem que la particio es diu sda1
#joe /etc/fstab (com root)
/dev/sda1       /media/windows    ntfs    defaults        0       0
(ctlr+k+x, per soritr i guardar els canvis)

3º vas al directori on vols que es munti la particio
# cd /media (o un altre si prefereixes)
# mkdir windows

4º muntes 
# mount -a

---

