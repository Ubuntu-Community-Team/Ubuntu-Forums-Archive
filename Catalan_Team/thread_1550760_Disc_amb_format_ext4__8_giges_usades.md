---
title: "Disc amb format ext4  8 giges usades ?"
date: 2010-08-11
forum: Catalan Team
---

### Post by CrIlat on 2010-08-11
Hola, bona tarda tinc un dubte que no se si es gaire normal. Per aixo vull que em dieu si estic errat. 
Estic reinstal·lant per desgracia win7 y ubuntu Lucid.
  Tinc un disc dur de 500 giges que es un vull posar ubuntu amb les particions correctament assignades. / swap /home. Estic ara mateix amb el gparted live i veig després de donar-li format ext4 al disc em diu que tinc un espai disponible de 465.76 GiB. Peró al donar-li el format ext4, em diu que tinc 7,5 GiB usades i em queda 458.26 GiB  ? es normal aixo que ocupi tantes giges si esta vuit?

Un salut.:(

---

### Post by urimax on 2010-08-15
Ningú t'ha contestat? deuen estar de vacances ;)

Aquesta la sé jo ^_^ primer post donant servei :D

El sistema d'arxius ext té una protecció en forma d'espai reservat pel sistema per evitar que accidentalment una partició pugui quedar plena (això pot donar força problemes a qualsevol sistema operatiu).

Pots canviar aquesta quantitat d'assignació amb la utilitat tune2fs. Per exemple, passar del 5% per defecte a un 1% (també accepta decimals, tipus 0.1) tan sols cal posar això en una consola (canviar /dev/sda1 per la partició que vulguis):

$sudo tune2fs -m1 /dev/sda1

Ho vaig necessitar en discos de 1.5Tb, on la quantitat ja la considero excessiva i més si són particions per sols emmagatzemar dades.

Més info d'un man tune2fs:
-m reserved-blocks-percentage

Set the percentage of the filesystem which may only be allocated by privileged processes. Reserving some number  of  filesystem blocks for use by privileged processes is done to avoid filesystem fragmentation, and to allow system  daemons,  such  as  syslogd(8),  to continue to function correctly after non-privileged processes are prevented from writing to  the  filesystem.Normally, the default percentage of reserved blocks is 5%.

---

### Post by CrIlat on 2010-08-17
Moltes gracies Urimax per respondre la dubte que tenia faré  servir el tune2fs a veure si no es gaire difícil de fer anar.
I si crec que la gent esta de vacances però la veritat es que em va sobtar que em volessin casi 8 gigues de cop xD.. 

Un salut i gracies per les aclariments.

---

