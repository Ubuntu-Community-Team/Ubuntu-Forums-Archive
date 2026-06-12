---
title: "partition problem"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by plante_ca on 2008-01-20
After creating Ubuntu on My C: and repearing a USB disk , i cant see this external disk any more...
 On Wondows XP and on Ubuntu  

here what i receive  on fdisk...

michel@michel-desktop:~$ sudo fdisk -l
[sudo] password for michel:

Disque /dev/sda: 200.0 Go, 200049647616 octets
240 heads, 63 sectors/track, 25841 cylinders
Units = cylindres of 15120 * 512 = 7741440 bytes
Disk identifier: 0x15ff15fe

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1         914     6909808+   c  W95 FAT32 (LBA)
/dev/sda2   *         915       23133   167975640    7  HPFS/NTFS
/dev/sda3           23134       23391     1950480   82  Linux swap / Solaris
/dev/sda4           23392       25841    18522000   83  Linux
AVERTISSEMENT: fanion 0x0000 invalide de la table de partitions 5 sera corrigé par w(écriture)

Disque /dev/sdb: 250.0 Go, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb2               1       30401   244196001    f  W95 Etendu (LBA)


I want to know how to repeare this...

**AVERTISSEMENT: fanion 0x0000 invalide de la table de partitions 5 sera corrigé par w(écriture)**

Ty

---

### Post by plante_ca on 2008-01-20
Want i do mount  i have this....

michel@michel-desktop:~$ mount
**/dev/sda4 on / type ext3 (rw,errors=remount-ro)**
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
michel@michel-desktop:~$


i do what with the bold line!

---

