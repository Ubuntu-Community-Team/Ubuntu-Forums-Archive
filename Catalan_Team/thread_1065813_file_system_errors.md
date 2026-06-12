---
title: "file system errors"
date: 2009-02-10
forum: Catalan Team
---

### Post by tanreb20 on 2009-02-10
Hola..

A l'ordinador central de casa(el que fa servir al mare i x aixo si no funciona tots hem de corre...) Fa uns dies que cada 3 o 4 dies doan aquest error en iniciar el pc:

/dev/sda1 contains a file system with errors, check forced.

Jo faig un fsck al /dev/sda1 i li dic que m'ho arregli tot.

Pero al cap de poc torna a fallar... Jo si estic a casa rai pero quan no i soc el smeus apres no saben que fer...

Qure pot ser la causa d'aixo? Jo sospito que el disc dur esat espatllat o tocat.. pero ni idea..

Algun IDEA?

---

### Post by oriolsbd on 2009-02-10
Quin format té la partició? ext3, ntfs, ...?

Salut!

---

### Post by papapep on 2009-02-10
> Algun IDEA?

1.- Aquest disc està en procés de defunció (Aka, ves-ne comprant un...)
2.- Fes una còpia de seguretat ARA millor que d'aquí cinc minuts. 

:-)

---

### Post by tanreb20 on 2009-02-10
sistema d'arxius ext3

papapep --> no hi ha cap cosa "important" en aquell ordiandorXD

---

### Post by papapep on 2009-02-10
> papapep --> no hi ha cap cosa "important" en aquell ordiandorXD 

Doncs:

1.- Executa unes quantes hores una de les utilitats que el fabricant facilitat per verificar l'estat físic del disc dur.

2.- Com que, probablement, està fotut, compra'n un de nou.

3.- Instal·la la variant d'ubuntu que més pes et faci de cap i de nou al nou disc dur.

Assumpte resolt.

---

### Post by tanreb20 on 2009-02-10
uhm.. hi ha alguna d'aquestes utilitats per linux? :P

---

### Post by torracastanyes on 2009-02-11
Aquestes utilitats solen ser live-cds, per tant no té res a veure el sistema operatiu (No tindría gaire sentit intentar instalar-la en un disc que no funciona).
La pots trobar a la web del fabricant del teu disc o bé en distribucions o "suites" de gestió de discos que corren per internet.

---

### Post by CarlesOriol on 2009-02-14
IDEA:

Usa les smartmontools per saber l'estat del disc. (instala > apt-get install smartmontools)

Si el disc t'està donant errors físics pots veure-ho amb 

sudo smartctl -a /dev/sda 

(sda sdb o el que sigui ....)

si vols forçar operacions al disc per tal de provar de generar un error

sudo smartctl -t short /dev/sda

(el short triga un minut o dos. Quan et torna el control no vol dir que hagi acabat. El long pren una hora)


després fas el control i mires com ha anat.

El s.m.a.r.t. sols comprova l'estat del disc. Sempre pot haver problemes amb la controladora / cables, etc... que no pots veure amb aquesta utilitat.

---

### Post by indiosincracia on 2009-02-28
El disc dur està fotut, sempre va bé tenir a mà el (GParted Live CD), amb fluxbox, s'inicia molt ràpidament i amb totes les particions desmontades, es pot reparar temporalment, però com indiquen els companys el millor és canviar-lo.

Pels frikis i discjockeys aquí tenim una perla:

[http://datacent.com/hard_drive_sounds.php](http://datacent.com/hard_drive_sounds.php)
  
Es tracta d'un recull de sons que solen fer els disc durs espatllats, ei! tenen força ritme...

---

