---
title: "usb  devices partly detected"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by francesco44 on 2007-03-10
I have installed Dapper  6.06 on a desktop with no problem: all my usb devices are detected and mounted;

I have installed Edgy 6.10 on my laptop IBM X30, when I plug USB devices, three different cases
1-an Intuix key is not detected and not mounted, the led does'nt lit,
2-an bytestore key with two partition, one partition under unix file system called casper, a second partition: both partitions appear in nautilus only casper is mounted
3-Memup small 5Go HD is detected, can be seen in nautilus with his name, but impossible to mount

**_Diagnostic for Bytestore case 2:_**

francesco@francesco-laptop:~$ dmesg|tail
[17181640.316000] sda: Mode Sense: 23 00 00 00
[17181640.316000] sda: assuming drive cache: write through
[17181640.316000]  sda: sda1 sda2
[17181640.320000] sd 2:0:0:0: Attached scsi removable disk sda
[17181640.320000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17181643.728000] UDF-fs: No VRS found
[17181643.984000] Unable to identify CD-ROM format.
[17181644.384000] kjournald starting.  Commit interval 5 seconds
[17181644.396000] EXT3 FS on sda2, internal journal
[17181644.396000] EXT3-fs: mounted filesystem with ordered data mode.

sudo fdisk -l ......shows (sorry its in french but I think you will understand)

Disque /dev/hda: 40.0 Go, 40007761920 octets
255 têtes, 63 secteurs/piste, 4864 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1   *           1        4774    38347123+  83  Linux
/dev/hda2            4775        4864      722925    5  Extended
/dev/hda5            4775        4864      722893+  82  Linux swap / Solaris

Disque /dev/sda: 2056 Mo, 2056257536 octets
255 têtes, 63 secteurs/piste, 249 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1          96      771088+   6  FAT16
/dev/sda2              97         249     1228972+  83  Linux

[B][U]
Diagnostic for MEMUP case 3[/U][/B]
dsmeg|tail gives:
francesco@francesco-laptop:~$ dmesg|tail
[17180948.152000] sda: test WP failed, assume Write Enabled
[17180948.152000] sda: assuming drive cache: write through
[17180948.160000] SCSI device sda: 7999488 512-byte hdwr sectors (4096 MB)
[17180948.164000] sda: test WP failed, assume Write Enabled
[17180948.164000] sda: assuming drive cache: write through
[17180948.164000]  sda: sda1
[17180948.200000] sd 1:0:0:0: Attached scsi disk sda
[17180948.200000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17180951.216000] UDF-fs: No VRS found
[17180951.484000] Unable to identify CD-ROM format.
francesco@francesco-laptop:~$ 



sudo fdisk -l ......shows (sorry its in french)

Disque /dev/hda: 40.0 Go, 40007761920 octets
255 têtes, 63 secteurs/piste, 4864 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1   *           1        4774    38347123+  83  Linux
/dev/hda2            4775        4864      722925    5  Extended
/dev/hda5            4775        4864      722893+  82  Linux swap / Solaris

Disque /dev/sda: 4095 Mo, 4095737856 octets
128 têtes, 63 secteurs/piste, 992 cylindres
Unités = cylindres de 8064 * 512 = 4128768 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1         992     3999712+   b  W95 FAT32
francesco@francesco-laptop:~$

---

