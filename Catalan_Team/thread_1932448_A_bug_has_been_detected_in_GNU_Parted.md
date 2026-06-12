---
title: "A bug has been detected in GNU Parted"
date: 2012-02-27
forum: Catalan Team
---

### Post by jinglada on 2012-02-27
El comanament *sudo fdisk -l* em dona aquest bug pel que fa al HD extern:
---------------------------------------------------------
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1      121602   976768033    7  HPFS/NTFS
Warning: Partition 1 does not end on cylinder boundary.
Error: /dev/sdc: unrecognised disk label
Backtrace has 12 calls on stack:
  12: /lib/libparted.so.0(ped_assert+0x31) [0x7f045d22d771]
  11: /lib/libparted.so.0(+0x3a14a) [0x7f045d25814a]
  10: /lib/libparted.so.0(+0x3a933) [0x7f045d258933]
  9: /lib/libparted.so.0(+0x3b5ed) [0x7f045d2595ed]
  8: /lib/libparted.so.0(ped_disk_add_partition+0x1cb) [0x7f045d233e7b]
  7: /lib/libparted.so.0(+0x3c9f6) [0x7f045d25a9f6]
  6: /lib/libparted.so.0(+0x3cba5) [0x7f045d25aba5]
  5: /lib/libparted.so.0(ped_disk_new+0x75) [0x7f045d234955]
  4: fdisk() [0x4088f4]
  3: fdisk() [0x4089dd]
  2: /lib/libc.so.6(__libc_start_main+0xfd) [0x7f045c62cc4d]
  1: fdisk() [0x4041c9]
A bug has been detected in GNU Parted.  Refer to the web site of parted [http://www.gnu.org/software/parted/parted.html](http://www.gnu.org/software/parted/parted.html) for more information of what could be useful for bug submitting!  Please email a bug report to [email]bug-parted@gnu.org[/email] containing at least the version (2.2) and the following message:  Assertion ((C * heads + H) * sectors + S == A) at ../../../libparted/labels/dos.c:679 in function probe_partition_for_geom() failed.
Avortat
------------------------------
He de fer alguna cosa?

---

### Post by jinglada on 2012-02-27
Ara veig que es tracta del HD del DVD que el tinc connectat fent-se la imatge amb el *ddrescue* per a recuperar els vídeos amb el *photorec*. 
He tornat a passar el *sudo fdisk -l* i ara em dóna això:

joan@joan-laptop:~$ sudo fdisk -l
[sudo] password for joan: 

Disk /dev/sda: 320 GB, 320070320640 bytes   ** -------> (HD intern)**
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

Disk /dev/sdb: 1000 GB, 1000202273280 bytes   ** -------> (HD extern de backup)**
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1      121602   976768033    7  HPFS/NTFS
Warning: Partition 1 does not end on cylinder boundary.
Error: /dev/sdc: unrecognised disk label    **------>   (HD del DVD)**

i no m'ha donat el backtrace d'abans ni el bug tampoc :-(

---

