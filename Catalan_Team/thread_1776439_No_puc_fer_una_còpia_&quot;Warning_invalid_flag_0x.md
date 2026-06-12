---
title: "No puc fer una còpia &quot;Warning: invalid flag 0x0000&quot;"
date: 2011-06-06
forum: Catalan Team
---

### Post by indiosincracia on 2011-06-06
hola,
ahir vaig intentar fer una còpia rutinària des-de el CD-Live (kubuntu 10.04 LTS) utilitzant la comanda "dd", amb el resultant error:

> ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=/dev/sdb bs=1M
dd: reading `/dev/sda': Input/output error
857+1 records in
857+1 records out
898838528 bytes (899 MB) copied, 71.1152 s, 12.6 MB/s
ubuntu@ubuntu:~$ 

repassant el sudo "fdisk -l" hi ha una línia inquietant que diu:
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000473dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37437   300709888   83  Linux
/dev/sda2           37437       38914    11858945    5  Extended
/dev/sda5           37437       38914    11858944   82  Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000473dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37437   300709888   83  Linux
/dev/sdb2           37437       38914    11858945    5  Extended

fdisk -l amb el disk engegat no surt

> volem@paamboli:~$ sudo fdisk -l
[sudo] password for volem: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e4c52

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37437   300709888   83  Linux
/dev/sda2           37437       38914    11858945    5  Extended
/dev/sda5           37437       38914    11858944   82  Linux swap / Solaris
volem@paamboli:~$ 

---

### Post by wgarcia on 2011-06-06
Potser forçant una verificació de disc es corregeixi això. Per forçar-la es pot fer des d'una terminal

sudo touch /forcefsck

i a la propera arrencada es verificarà el disc.

---

### Post by indiosincracia on 2011-06-09
desprès de fer això la verificació ha estat molt ràpida i s'ha engegat normalment, l'he reiniciat i desprès del grub s'ha quedat congelat amb un guió blanc a la part superior esquerra, he fet "alt+pet sis reisub" i s'ha reiniciat
el disc de 500 g l'he formatejat amb el gparted, i un altre cop des-de cd-Live
sudo dd if=/dev/sda of=/dev/sdb bs=1M
s'ha quedat congelat

---

### Post by wgarcia on 2011-06-10
Entenc que ja s'inicia normalment? Has tornat a provar el "fdisk -l" per veure si continua sortint el missatge del "flag"?

---

### Post by indiosincracia on 2011-06-10
desde el disc 320G

> volem@paamboli:~$ sudo fdisk -l
[sudo] password for volem: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e4c52

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37437   300709888   83  Linux
/dev/sda2           37437       38914    11858945    5  Extended
/dev/sda5           37437       38914    11858944   82  Linux swap / Solaris




desde cd-live al disk 500G



> 
ubuntu@ubuntu:~$ sudo fdisk -l
Atención: el indicador 0x0000 inválido de la tabla de particiones 5 se corregirá mediante w(rite)

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x000e4c52

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       37437   300709888   83  Linux
/dev/sda2           37437       38914    11858945    5  Extendida

---

### Post by wgarcia on 2011-06-10
El que no m'ha quedat clar al teu missatge #3 és si el sistema s'inicia normalment o es queda congelat, o sols es queda congelat amb la instrucció "dd".

---

### Post by indiosincracia on 2011-06-10
nomès amb l'ordre dd

ho he tornat a provar ara, engegant des-de el CD-Live i els dos discs conectats:

sudo dd if=/dev/sda of=/dev/sdb

congelat als 5 minuts

---

### Post by wgarcia on 2011-06-10
Segons el que diuen els fdisk -l que poses al missatge #5 el dispositiu /dev/sdb ara no l'està veient el sistema. És un disc USB o un disc intern?

---

### Post by indiosincracia on 2011-06-10
perdó l'havia tret, és un disc intern.

> volem@paamboli:~$ sudo fdisk -l
[sudo] password for volem: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e4c52

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37437   300709888   83  Linux
/dev/sda2           37437       38914    11858945    5  Extended
/dev/sda5           37437       38914    11858944   82  Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e4c52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37437   300709888   83  Linux
/dev/sdb2           37437       38914    11858945    5  Extended
volem@paamboli:~$

---

### Post by wgarcia on 2011-06-10
No sóc un expert de "dd", però el disc /dev/sdb no hauria d'estar sense particions? Potser algun altre més coneixedor podria ajudar.

---

### Post by kukat on 2011-06-12
Has provat a fer-ho amb un altre Live CD que siga més lleuger??? 


Per cert, ací hi ha unes instruccions amb el DD molt interessants, sobretot la de compressió amb Gzip: 

[http://en.opensuse.org/SDB:Home_backup#dd](http://en.opensuse.org/SDB:Home_backup#dd)

---

