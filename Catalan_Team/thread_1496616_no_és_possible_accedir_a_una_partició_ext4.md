---
title: "no és possible accedir a una partició ext4"
date: 2010-05-29
forum: Catalan Team
---

### Post by albert-I on 2010-05-29
Bon dia
Amb el nou 10.04 volia fer una prova fer una nova instal·lació del kubuntu i la vaig fer des de nou, i per tant des de una live vaig reordenar una mica les particions del disk (aquí pot ser l'error) i vaig fer la instal·lació, però on tenia el /home, que és la sdb6 però em surt un error.
Em principi entenc que es un error en la partició, com una corrupció de la partició i que no hi ha possibilitats de resurrecció.
No se si vaig equivocat i hi ha una solució per resoldre aquest problema.


I moltes gràcies a tothom

fdisk -l
 
Disc /dev/sdb: 250.1 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e2758

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb2   *           1       30401   244195939    5  Estesa
/dev/sdb5           29764       30401     5124735   82  Intercanvi Linux / Solaris
/dev/sdb6               1       27847   223680932   83  Linux
/dev/sdb7           27848       29763    15390238+  83  Linux

I això es del syslog

May 29 18:17:02 desktop CRON[15797]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 29 18:17:24 desktop kernel: [ 2576.421052] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 18:17:24 desktop kernel: [ 2576.421059] EXT4-fs (sdb6): group descriptors corrupted!
May 29 18:19:01 desktop kernel: [ 2673.238941] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 18:19:01 desktop kernel: [ 2673.238949] EXT4-fs (sdb6): group descriptors corrupted!
May 29 18:30:26 desktop kernel: [ 3358.452775] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 18:30:26 desktop kernel: [ 3358.452782] EXT4-fs (sdb6): group descriptors corrupted!
May 29 18:30:41 desktop kernel: [ 3373.267927] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 18:30:41 desktop kernel: [ 3373.267936] EXT4-fs (sdb6): group descriptors corrupted!
May 29 18:30:45 desktop kernel: [ 3377.390433] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 18:30:45 desktop kernel: [ 3377.390442] EXT4-fs (sdb6): group descriptors corrupted!
May 29 18:30:46 desktop hald: mounted /dev/sda1 on behalf of uid 0
May 29 18:30:46 desktop ntfs-3g[16007]: Version 2010.3.6 external FUSE 28
May 29 18:30:46 desktop ntfs-3g[16007]: Mounted /dev/sda1 (Read-Write, label "System Reserved", NTFS 3.1)
May 29 18:30:46 desktop ntfs-3g[16007]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=ca_ES.UTF-8
May 29 18:30:46 desktop ntfs-3g[16007]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
May 29 18:30:46 desktop ntfs-3g[16007]: Ownership and permissions disabled, configuration type 1
May 29 18:30:50 desktop kernel: [ 3382.429074] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 18:30:50 desktop kernel: [ 3382.429082] EXT4-fs (sdb6): group descriptors corrupted!
May 29 18:30:51 desktop kernel: [ 3384.153152] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 18:30:51 desktop kernel: [ 3384.153160] EXT4-fs (sdb6): group descriptors corrupted!
May 29 18:30:53 desktop kernel: [ 3385.260940] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 18:30:53 desktop kernel: [ 3385.260948] EXT4-fs (sdb6): group descriptors corrupted!
May 29 18:30:55 desktop kernel: [ 3387.376177] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 18:30:55 desktop kernel: [ 3387.376185] EXT4-fs (sdb6): group descriptors corrupted!
May 29 18:31:02 desktop kernel: [ 3394.838499] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 18:31:02 desktop kernel: [ 3394.838507] EXT4-fs (sdb6): group descriptors corrupted!
May 29 18:31:10 desktop kernel: [ 3402.517266] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 18:31:10 desktop kernel: [ 3402.517274] EXT4-fs (sdb6): group descriptors corrupted!
May 29 18:50:07 desktop kernel: [ 4540.040032] usb 1-2: new high speed USB device using ehci_hcd and address 2
May 29 18:50:07 desktop kernel: [ 4540.192910] usb 1-2: configuration #1 chosen from 1 choice
May 29 18:50:07 desktop kernel: [ 4540.193194] scsi9 : SCSI emulation for USB Mass Storage devices
May 29 18:50:07 desktop kernel: [ 4540.193323] usb-storage: device found at 2
May 29 18:50:07 desktop kernel: [ 4540.193327] usb-storage: waiting for device to settle before scanning
May 29 18:50:12 desktop kernel: [ 4545.190239] usb-storage: device scan complete
May 29 18:50:12 desktop kernel: [ 4545.191082] scsi 9:0:0:0: Direct-Access     USB 2.0  Flash Drive      2.00 PQ: 0 ANSI: 2
May 29 18:50:12 desktop kernel: [ 4545.191685] sd 9:0:0:0: Attached scsi generic sg4 type 0
May 29 18:50:13 desktop kernel: [ 4545.954358] sd 9:0:0:0: [sdd] 512000 512-byte logical blocks: (262 MB/250 MiB)
May 29 18:50:13 desktop kernel: [ 4545.954851] sd 9:0:0:0: [sdd] Write Protect is off
May 29 18:50:13 desktop kernel: [ 4545.954855] sd 9:0:0:0: [sdd] Mode Sense: 03 00 00 00
May 29 18:50:13 desktop kernel: [ 4545.954858] sd 9:0:0:0: [sdd] Assuming drive cache: write through
May 29 18:50:13 desktop kernel: [ 4545.956975] sd 9:0:0:0: [sdd] Assuming drive cache: write through
May 29 18:50:13 desktop kernel: [ 4545.956980]  sdd: sdd1
May 29 18:50:13 desktop kernel: [ 4545.960240] sd 9:0:0:0: [sdd] Assuming drive cache: write through
May 29 18:50:13 desktop kernel: [ 4545.960245] sd 9:0:0:0: [sdd] Attached SCSI removable disk
May 29 18:50:22 desktop hald: mounted /dev/sdd1 on behalf of uid 1000
May 29 19:10:11 desktop kernel: [ 5743.892221] usb 1-1: new high speed USB device using ehci_hcd and address 3
May 29 19:10:11 desktop kernel: [ 5744.046357] usb 1-1: configuration #1 chosen from 1 choice
May 29 19:10:11 desktop kernel: [ 5744.047340] scsi10 : SCSI emulation for USB Mass Storage devices
May 29 19:10:11 desktop kernel: [ 5744.047474] usb-storage: device found at 3
May 29 19:10:11 desktop kernel: [ 5744.047476] usb-storage: waiting for device to settle before scanning
May 29 19:10:15 desktop kernel: [ 5748.092259] usb 1-1: USB disconnect, address 3
May 29 19:17:01 desktop CRON[16939]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 29 19:53:10 desktop kernel: [ 8322.417340] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 19:53:10 desktop kernel: [ 8322.417347] EXT4-fs (sdb6): group descriptors corrupted!
May 29 19:54:10 desktop kernel: [ 8382.297975] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 19:54:10 desktop kernel: [ 8382.297983] EXT4-fs (sdb6): group descriptors corrupted!
May 29 19:54:21 desktop kernel: [ 8394.140628] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 19:54:21 desktop kernel: [ 8394.140637] EXT4-fs (sdb6): group descriptors corrupted!
May 29 19:54:22 desktop kernel: [ 8394.732090] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 19:54:22 desktop kernel: [ 8394.732099] EXT4-fs (sdb6): group descriptors corrupted!
May 29 19:54:44 desktop kernel: [ 8416.552398] EXT4-fs (sdb6): ext4_check_descriptors: Checksum for group 1152 failed (8!=24)
May 29 19:54:44 desktop kernel: [ 8416.552406] EXT4-fs (sdb6): group descriptors corrupted!

---

### Post by wgarcia on 2010-05-30
Potser el superbloc de la partició s'hagi danyat amb les teves modificacions a la partició. Per verificar això, pots intentar la següent instrucció accedint a una terminal de comandes (no sé si tens accés en començar o des d'un CD live d'instal·lació):

sudo fsck.ext4 -v /dev/sdb6

i posa aquí el que surti.

---

### Post by albert-I on 2010-06-02
Gràcies, moltes gràcies, doncs ara puc entrar! 

Al posar la línia, em deia que hi havia molts sectors danyats i si ho volia arreglar, inconscientment, li doncs que sí (com si jo pogues arreglar quelcom) i al cap d'una estona surt això, tot seguit he provat de anar-hi amb el dolphin i hi he pogut accedir.

Per tant suposo que això estarà arreglat?
ara al fstab hi posarè la nova /home i segurament tot està arreglat.


) -8781626 -(8781628--8781632)
Arregla<s>? sí


/dev/sdb6: ***** S'HA MODIFICAT EL SISTEMA DE FITXERS *****

   50236 inodes used (0.55%)
     277 non-contiguous files (0.6%)
      28 non-contiguous directories (0.1%)
     nombre de nodes-i amb blocs ind/dind/tind: 0/0/0
         Extent depth histogram: 50062/94
17170323 blocks used (47.21%)
       0 bad blocks
       2 large files

   48114 regular files
    1868 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
     242 symbolic links (67 fast symbolic links)
       3 sockets
--------
   50227 files


I ara tot i que no surt al fstab ja hi puc accedir, que es molt. ara em toca investigar una mica per veure com haig de deixar el fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=93c2fa34-5dc7-4e9a-9ad9-12bda5741e04 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=bd00e1b8-9545-4556-8f84-a8113ab723e3 none            swap    sw              0       0

---

### Post by albert-I on 2010-06-02
Ara sols falta que trobi el mitja que sigui accessible como a /home aquesta partició. Donc com a resolta la pregunta o espero acabar de fer la recuperació??

---

### Post by wgarcia on 2010-06-02
A aquesta partició tenies muntat el /home? Si fos així es tractaria de restablir el punt de muntatge que tenies.

---

### Post by albert-I on 2010-06-02
Si abans tenia el /home separat, el que passa es que al fer la instal·lació del nou sistema em va petar per l'error del superblock i ara mateix tinc instal·lat el /home junt amb la partició.

Pel que fa ho de restablir els punt de muntatge. A que et refereixes, exactament? Pensa amb el meu complet desconeixement de moltes coses, de us no habitual o coses basiques.

---

### Post by wgarcia on 2010-06-02
Per accedir al contingut de la partició /dev/sdb7 has d'establir un punt de muntatge a ella, però ara mateix ja no sé ben bé com ho tens organitzat, si aquesta és una partició extendida. Potser si mostres com ho veu el gparted (Sistema - Gestor de particions, penso) es podrà veure com tens definides totes les particions, les que tens muntades i les que no.

---

### Post by albert-I on 2010-06-04
Està en una partició lògica, com és pot comprovar amb la foto afegida.

Moltes gràcies per la teva atenció.

---

### Post by wgarcia on 2010-06-04
Has de crear un punt de muntatge de /home a l'arxiu "fstab". Per veure el UUID de la partició fes

sudo blkid

i mira l'entrada per a /dev/sdb6. Per exemple:

/dev/sdb6: UUID="df7b0eb7-2015-4247-be96-e2ef8e6227c5" TYPE="ext4"

Óbviament el teu UUID serà diferent.

Després edita l'arxiu /etc/fstab i entres les 2 línies següents, canviant l'UUID pel que t'hagi sortit (la primera línia és optativa, és per recordar de quina partició es tracta):

#/dev/sdb6
UUID=df7b0eb7-2015-4247-be96-e2ef8e6227c5  /home  ext4 relatime,errors=remount-ro 0       2

---

### Post by albert-I on 2010-06-05
Moltes gràcies, ja està resolt

---

