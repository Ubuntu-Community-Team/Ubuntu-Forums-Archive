---
title: "reparació targeta gràfica"
date: 2012-09-14
forum: Catalan Team
---

### Post by jinglada on 2012-09-14
Benvolguts experts ubunterus:

Al meu Packard Bell Easynote MT85-M-005SP, Intel Core 2 Duo P8400 2.26 GHz, Ram 4 Gb DDR2, ATI HD3650 512 MB, Hard Drive 320 GB, amb el Lucid Linx, se li va apagar la pantalla.

Després de "reparar-me" la targeta gràfica per 158,61 €, iva inclòs, m'arriba el portàtil i tinc els següents problemes:

En engegar em surt la següent pantalla:

[IMG]http://ubuntuforums.org/picture.php?albumid=2498&pictureid=8483[/IMG]

premo F1, s'inicia la verificació d'errors del disc i quan arriba al 67% em surt aquest altre missatge:

[IMG]http://ubuntuforums.org/picture.php?albumid=2498&pictureid=8484[/IMG]

Com que no veig quina tecla he de prèmer per corregir els errors, premo "I" per a ignorar-los.

Què hauria de fer per a solucionar-ho?

Gràcies per endavant!

---

### Post by wgarcia on 2012-09-14
Per al missatge que surt al peu de la primera pantalla, sembla un problema de la configuració del BIOS, potser si entres al "Setup" et deixa fixar el dia/hora com et demana.

Per la segona pantalla:

El que no veus diu "M per fer una recuperació manual" o una cosa així. 

El que pot passar és que el sistema de fitxers no s'ha tancat correctament, i el sistema ha de fer una comprovació d'errors del disc abans de muntar-los. 

El que pots fer és prémer "M" i t'enviarà a una línia de comandes. Per fer la comprovació i correcció d'errors del disc, pots fer
```
fsck /dev/sda1
```

si /dev/sda1 és el dispositiu on tens la partició d'arrencada (/boot). Per veure si aquest és el cas pots fer 
```
fdisk -l
```
t'ensenyarà la partició d'arrencada amb un asterisc.

La primera instrucció et farà una sèrie de preguntes que en principi pots contestar que sí.

---

### Post by jinglada on 2012-09-15
Gràcies wgarcia. 

Pel que fa al primer missatge, estava tan nerviós que no vaig llegir que havia de fer "setup" per posar dia i hora. De fet vaig crear un directori abans de connectar-me a internet i em va estranyar que el va crear amb data 2-9-2008.

Pel que fa al segon missatge, faig el que em dius per determinar la /boot i no em dóna res :-(

joan@joan-laptop:~$ fdisk -l
joan@joan-laptop:~$

Amb el GParted veig que el /boot és la sda2.

[http://ubuntuforums.org/picture.php?albumid=2498&pictureid=8485](http://ubuntuforums.org/picture.php?albumid=2498&pictureid=8485)

Faig "fsck /dev/sda2" ?

---

### Post by wgarcia on 2012-09-15
Sí, però per assegurar-te i que et funcioni el "fdisk" posa-li un "sudo" endavant, o sigui

```
sudo fdisk -l
```

---

### Post by jinglada on 2012-09-15
> **wgarcia said:**
> Sí, però per assegurar-te i que et funcioni el "fdisk" posa-li un "sudo" endavant, o sigui

```
sudo fdisk -l
```

Ara si:

joan@joan-laptop:~$ sudo fdisk -l
[sudo] password for joan: 

Disk /dev/sda: 320 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1        1567    12586896    7  HPFS/NTFS
/dev/sda2   *        1568        6193    37150312    7  HPFS/NTFS
/dev/sda3            6194       38913   262815367    5  Extended
/dev/sda6            6194       11056    39054015   83  Linux
Warning: Partition 6 does not end on cylinder boundary.
/dev/sda7           11057       37582   213062062   83  Linux
Warning: Partition 7 does not end on cylinder boundary.
/dev/sda5           37583       38913    10683225   82  Linux swap
Warning: Partition 5 does not end on cylinder boundary.
-------------------------------------------------------

Els tres "Warning" són preocupants?

---

### Post by jinglada on 2012-09-15
El /boot que té l'etiqueta HDD, crec que és on hi tinc el Windows:

joan@joan-laptop:/media/HDD$ ls -l
total 3451639
lrwxrwxrwx 2 joan joan         92 2009-03-12 17:20 Archivos de programa -> /media/HDD/Program Files
-rwxrwxrwx 1 joan joan         24 2006-09-18 23:43 autoexec.bat
drwx------ 1 joan joan       4096 2010-02-12 18:23 boot
-rwxrwxrwx 1 joan joan     333257 2009-04-11 08:36 bootmgr
-rwxrwxrwx 1 joan joan       8192 2008-10-11 23:58 BOOTSECT.BAK
drwx------ 1 joan joan       4096 2012-08-29 02:20 Config.Msi
-rwxrwxrwx 3 joan joan         10 2006-09-18 23:43 config.sys
lrwxrwxrwx 2 joan joan         60 2006-11-02 14:02 Documents and Settings -> /media/HDD/Users
drwx------ 1 joan joan       4096 2009-03-13 01:11 drivers
-rwxrwxrwx 1 joan joan       2916 2008-04-23 17:10 files.crc
drwx------ 1 joan joan          0 2008-10-11 14:29 Intel
drwx------ 1 joan joan      20480 2011-03-24 21:24 JBS0ESW2
-rwxrwxrwx 1 joan joan 3534004224 2008-09-02 00:01 pagefile.sys
drwx------ 1 joan joan          0 2008-01-21 03:32 PerfLogs
drwx------ 1 joan joan       8192 2012-05-15 22:10 ProgramData
drwx------ 1 joan joan      24576 2012-05-15 21:31 Program Files
drwx------ 1 joan joan          0 2009-03-12 17:38 $Recycle.Bin
-rwxrwxrwx 1 joan joan        650 2008-10-11 14:37 RHDSetup.log
-rwxrwxrwx 1 joan joan         86 2008-10-11 14:43 setup.log
drwx------ 1 joan joan      20480 2012-09-06 12:52 System Volume Information
-rwxrwxrwx 1 joan joan          0 2008-10-11 14:57 temp_ig.txt
-rwxrwxrwx 1 joan joan        771 1999-12-31 23:00 tmp1
-rwxrwxrwx 1 joan joan        128 1999-12-31 23:00 tmp2
drwx------ 1 joan joan       4096 2009-03-12 17:24 Users
drwx------ 1 joan joan      28672 2012-08-29 02:02 Windows

i al sda1, etiquetat _OEMBP, no sé què és i hi ha això:

joan@joan-laptop:/media/_OEMBP$ ls -l
total 139793
drwx------ 1 joan joan      4096 2008-10-12 00:15 boot
-rwxrwxrwx 1 joan joan    333203 2008-01-21 03:24 bootmgr
-rwxrwxrwx 1 joan joan   3170304 2008-01-03 11:23 boot.sdi
drwx------ 1 joan joan     12288 2011-03-24 18:05 config
-rwxrwxrwx 1 joan joan    431700 2009-03-12 17:25 crclog.dat
drwx------ 1 joan joan         0 2008-06-17 11:23 drivers
drwx------ 1 joan joan         0 2008-10-12 00:15 mcd
drwx------ 1 joan joan      8192 2008-10-12 01:10 recovery
drwx------ 1 joan joan         0 2009-03-12 22:11 $RECYCLE.BIN
-rwxrwxrwx 1 joan joan         2 2009-03-13 16:30 rmeddone.tag
drwx------ 1 joan joan      8192 2008-02-14 11:59 softsource
drwx------ 1 joan joan         0 2012-09-06 12:52 System Volume Information
drwx------ 1 joan joan     28672 2009-03-12 17:24 tools
drwx------ 1 joan joan      4096 2008-10-12 01:33 wim
-rwxrwxrwx 1 joan joan 139138833 2008-10-12 00:15 winre.wim

---

### Post by jinglada on 2012-09-15
Al directori /media/_OEMBP/boot hi ha:

joan@joan-laptop:/media/HDD/boot$ ls -l
total 4112
-rwxrwxrwx 1 joan joan   32768 2008-09-02 00:32 BCD
-rwxrwxrwx 1 joan joan  262144 2008-09-02 00:06 BCD.LOG
-rwxrwxrwx 2 joan joan       0 2008-10-11 23:58 BCD.LOG1
-rwxrwxrwx 2 joan joan       0 2008-10-11 23:58 BCD.LOG2
-rwxrwxrwx 2 joan joan  262144 2008-10-11 07:48 bcd.ramdisk
-rwxrwxrwx 1 joan joan    1024 2008-01-03 10:54 bootfix.bin
-rwxrwxrwx 1 joan joan 3170304 2008-01-03 11:23 boot.sdi
-rwxrwxrwx 1 joan joan   65536 2008-10-11 23:58 bootstat.dat
drwx------ 1 joan joan       0 2010-02-12 18:23 cs-CZ
drwx------ 1 joan joan       0 2010-02-12 18:23 da-DK
drwx------ 1 joan joan       0 2010-02-12 18:23 de-DE
drwx------ 1 joan joan       0 2010-02-12 18:23 el-GR
drwx------ 1 joan joan       0 2010-02-12 18:23 en-US
drwx------ 1 joan joan       0 2010-02-12 18:23 es-ES
-rwxrwxrwx 1 joan joan    2048 2008-01-05 03:23 etfsboot.com
drwx------ 1 joan joan       0 2010-02-12 18:23 fi-FI
drwx------ 1 joan joan       0 2008-10-11 23:58 fonts
drwx------ 1 joan joan       0 2010-02-12 18:23 fr-FR
drwx------ 1 joan joan       0 2010-02-12 18:23 hu-HU
drwx------ 1 joan joan       0 2010-02-12 18:23 it-IT
drwx------ 1 joan joan       0 2010-02-12 18:23 ja-JP
drwx------ 1 joan joan       0 2010-02-12 18:23 ko-KR
-rwxrwxrwx 1 joan joan  405992 2009-04-11 08:32 memtest.exe
drwx------ 1 joan joan       0 2010-02-12 18:23 nb-NO
drwx------ 1 joan joan       0 2010-02-12 18:23 nl-NL
drwx------ 1 joan joan       0 2010-02-12 18:23 pl-PL
drwx------ 1 joan joan       0 2010-02-12 18:23 pt-BR
drwx------ 1 joan joan       0 2010-02-12 18:23 pt-PT
drwx------ 1 joan joan       0 2010-02-12 18:23 ru-RU
drwx------ 1 joan joan       0 2010-02-12 18:23 sv-SE
drwx------ 1 joan joan       0 2010-02-12 18:23 tr-TR
drwx------ 1 joan joan       0 2010-02-12 18:23 zh-CN
drwx------ 1 joan joan       0 2010-02-12 18:23 zh-HK
drwx------ 1 joan joan       0 2010-02-12 18:23 zh-TW

---

### Post by wgarcia on 2012-09-15
/dev/sda2 sembla ser on tens instal·lat el windows i l'arrencada del sistema. 

Potser el millor és provar 
```
sudo fsck
```

sense arguments perquè es verifiqui tot el dispositiu i veure què diu. Si et diu que ha trobat algun error i si vols arreglar-ho, normalment és segur dir-li que sí, tot i que com sempre convé que tinguis còpia de seguretat de tots els documents i fitxers del disc, perquè els discos poden fallar. Tot i que seria força mala sort que t'hagués fallat la targeta gràfica i el disc alhora.

---

### Post by jinglada on 2012-09-15
Abans de llegir el teu missatge últim havia reiniciat, he arranjat la data i hora en el "setup" i després he premut la "M"quan s'ha parat dient que hi havia errors en el disc i he fet el "fsck /dev/sda2", que no ha avançat i m'ha donat el següent missatge:

fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2

provo el que dius "sudo fsck"?

---

### Post by jinglada on 2012-09-15
En relació als "warning" he trobat això:
[http://prefetch.net/blog/index.php/2009/09/12/why-partition-x-does-now-end-on-cylinder-boundary-warnings-dont-matter/](http://prefetch.net/blog/index.php/2009/09/12/why-partition-x-does-now-end-on-cylinder-boundary-warnings-dont-matter/)

he fet el que diu:

joan@joan-laptop:~$ sudo sfdisk -uS -l /dev/sda
[sudo] password for joan: 

Disc /dev/sda: 38913 cilindres, 255 capçals, 63 sectors/pista
Unitats = sectors de 512 octets, contant des de 0

Disp  Arr         Inici     Final   #sectors  Id  Sistema
/dev/sda1            63  25173854   25173792   7  HPFS/NTFS
/dev/sda2   *  25173855  99490544   74316690   7  HPFS/NTFS
/dev/sda3      99490545 625137344  525646800   5  Estesa
/dev/sda4             0         -          0   0  Buida
/dev/sda5     603754893 625137344   21382452  82  Intercanvi Linux / Solaris
/dev/sda6      99490671 177614639   78123969  83  Linux
/dev/sda7     177614703 603754829  426140127  83  Linux
joan@joan-laptop:~$ 


És correcte?

PS: No aconsegueixo encolumnar-ho

---

### Post by wgarcia on 2012-09-15
La veritat és que no ho sé, però jo he tingut aquest "warning" en alguns sistemes i mai no he tingut problemes degut a això que recordi.

---

### Post by jinglada on 2012-09-15
> **wgarcia said:**
> La veritat és que no ho sé, però jo he tingut aquest "warning" en alguns sistemes i mai no he tingut problemes degut a això que recordi.

A 3 webs que he consultat diuen que això no te importància perquè ...
----------------------------------------------------
els sistemes moderns usen LBA (Logical Block Addressing) en lloc de CHS (Cilindre / Capçal / Sector) per adreçar les unitats de disc.

[http://prefetch.net/blog/index.php/2009/09/12/why-partition-x-does-now-end-on-cylinder-boundary-warnings-dont-matter/](http://prefetch.net/blog/index.php/2009/09/12/why-partition-x-does-now-end-on-cylinder-boundary-warnings-dont-matter/)
-----------------------------------------------------
El concepte de "cilindres" no té sentit en els moderns discos LBA - encara menys en flash. Simplement per mantenir la compatibilitat. Estàs perseguint fum. ;-) diuen a:

[http://www.linuxquestions.org/questions/ubuntu-63/how-to-fix-partition-not-end-on-cylinder-boundary-768635/](http://www.linuxquestions.org/questions/ubuntu-63/how-to-fix-partition-not-end-on-cylinder-boundary-768635/)
----------------------------------------------------
No, no t'hauries de preocupar per això. Els cilindres són ficcions completes i cap sistema operatiu actual, ni tan sols MS-DOS, dona importància a això. És un missatge sense sentit del fdisk, que té més de tres anys per darrere d'un altra utilitat de partició de disc i no mostra signes de millora. Usa una eina actualitzada que no mostri aquesta fotesa... diu a:

[http://superuser.com/questions/339288/warning-partition-x-does-not-end-on-cylinder-boundary-should-i-care-how-to-fix](http://superuser.com/questions/339288/warning-partition-x-does-not-end-on-cylinder-boundary-should-i-care-how-to-fix)

---

### Post by jinglada on 2012-09-15
> **wgarcia said:**
> /dev/sda2 sembla ser on tens instal·lat el windows i l'arrencada del sistema. 

Potser el millor és provar 
```
sudo fsck
```

sense arguments perquè es verifiqui tot el dispositiu i veure què diu. Si et diu que ha trobat algun error i si vols arreglar-ho, normalment és segur dir-li que sí, tot i que com sempre convé que tinguis còpia de seguretat de tots els documents i fitxers del disc, perquè els discos poden fallar. Tot i que seria força mala sort que t'hagués fallat la targeta gràfica i el disc alhora.

Em sembla que ja està solucionat. "sudo fsck" m'ha donat aproximadament això:

Pas 1
Inode was part of the orphaned inode list. FIXED.
Deleted inode nnnn has zero dtime. Fix<y>? yes

Pas 2
Checking directory structure

Pas 3
Checking directory connectivity

Pas 4
Checking reference counts

Pas 5
Checking group summary information
Inode bitmap differences nnnn nnnn nnnn nnnn ... Fix <y>? yes

Pas 6
Free inodes count wrong for group (4171, counted=4186). Fix<y>? yes

Pas 7
Free inodes count wrong (1869017, counted=1859032). Fix<y>? yes

/dev/sda6: ***FILE SYSTEM WAS MODIFIED***
/dev/sda6: ***REBOOT LINUX***
/dev/sda6: 585592/2444624 files (1,9% non-contigous) 3720799/9765496 blocks

------------------------

He reiniciat i tot ha funcionat com abans.

He de fer alguna cosa més?

Moltes gràcies wgarcia!!!

---

### Post by wgarcia on 2012-09-16
Suposo que no, si tot va bé.

---

