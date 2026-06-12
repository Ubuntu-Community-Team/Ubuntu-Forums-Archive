---
title: "Mission Impossible"
date: 2013-11-17
forum: Apple Hardware Users
---

### Post by 1.rtansley on 2013-11-17
Please please help..i have a macbook pro and have mavericks,unbuntu and windows 7 installed. i have refit installed and after installing unbuntu my problems started. i tried to upgrade with refind and then i tried lots of different things. i have 6 bootup icons instead of 3 and i can not even start windows. please can anyone help i am overwhelmed totally!!!:(

Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libicu48:i386 libpopt0:i386 libstdc++6:i386
0 upgraded, 0 newly installed, 3 to remove and 23 not upgraded.
1 not fully installed or removed.
After this operation, 23.5 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 201250 files and directories currently installed.)
Removing libicu48:i386 ...
Removing libpopt0:i386 ...
Removing libstdc++6:i386 ...
Processing triggers for libc-bin ...
Setting up refind (0.7.5-1) ...
/var/lib/dpkg/info/refind.postinst: line 4: efibootmgr: command not found
Installing rEFInd on Linux....
//boot/efi doesn't seem to be on a VFAT filesystem. The ESP must be
mounted at //boot or //boot/efi and it must be VFAT! Aborting!
dpkg: error processing refind (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 refind
E: Sub-process /usr/bin/dpkg returned an error code (1)
robert@robert-MacBookPro:~$


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
Partition 1 does not start on physical sector boundary.
/dev/sda2          409640   489484247   244537304   af  HFS / HFS+
/dev/sda3       489746392   978558975   244406292   83  Linux
/dev/sda4   *   978821120  1465147391   243163136    7  HPFS/NTFS/exFAT

Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x58946bcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
Partition 1 does not start on physical sector boundary.
/dev/sda2          409640   489484247   244537304   af  HFS / HFS+
/dev/sda3       489746392   978558975   244406292   83  Linux
/dev/sda4   *   978821120  1465147391   243163136    7  HPFS/NTFS/exFAT
robert@robert-MacBookPro:~$ sudo parted /dev/sda print
Model: ATA APPLE HDD HTS547 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
 1      20.5kB  210MB  210MB  fat32        EFI System Partition  boot
 2      210MB   251GB  250GB  hfs+         Untitled
 3      251GB   501GB  250GB  ext2         linux
 4      501GB   750GB  249GB  ntfs         BOOTCAMP              msftdata

---

### Post by bapoumba on 2013-11-17
Moved to the Apple Users subforum.

---

### Post by 1.rtansley on 2013-11-17
can none of you help...i am totally new at linux and totally shocked that no one will even try and help me

obviously nobody knows how to do it

---

### Post by Iowan on 2013-11-17
Perhaps not - or perhaps your answer  lives in another time zone. Posting guidelines/courtesy dictate bumping a post only after 24 hours.

---

### Post by 1.rtansley on 2013-11-17
thanks admin,i do apologize...just really desperate

---

### Post by 1.rtansley on 2013-11-18
repaired my windows 7 boot with the repair disk, just need help sorting out the unbuntu bootup

---

### Post by 1.rtansley on 2013-11-18
ok i am a total unbuntu newbie and it looks incredible buuuuuuut when i boot up i have 2 images for unbuntu, 1 osx image, 2 useless penguins, and my windows7. total of 6 bootup images on a refit bootup screen. please can someone help, i can start unbuntu but it takes a few times to start it up. i think it was super boot manager that caused problems or the grub customiser i installed. just want to get everything back to normal. i know i messed it up and it has been a hard lesson that i will not make again!

---

