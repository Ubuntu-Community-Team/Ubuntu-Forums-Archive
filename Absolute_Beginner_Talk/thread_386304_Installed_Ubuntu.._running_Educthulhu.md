---
title: "Installed Ubuntu.. running Educthulhu?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Jormanks on 2007-03-16
Hi guys.... well.... I downloaded Ubuntu 6.10, the live CD, had troubles with the internet connection and, when i finally begin upgrading the whole thing, the next time i booted linux it was not Ubuntu but Edubuntu... well... why?

How can I reverse it?

Also I have troubles with a SATA partition: the first partition is recognized and mounted, but the other one is not... and is where i have my media files.... how can i fix that?

Thanks.

---

### Post by Skia_42 on 2007-03-16
Did you have edubuntu installed on a seperate partition?  As to the SATA partition, is it a windows partition with music on it? If so this [guide]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html") shows you how to mount it.

---

### Post by Jormanks on 2007-03-16
when i type mount into the terminal here's what it goes:
> 
/dev/hda2 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/hdb1 on /media/hdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


I can's see /dev/sda2, the other SATA partition I was talking about....
How can i find it?

And the Edubuntu... it was a trojan my mom likes to call "son", which is not me. My brother changed to edubuntu's theme...

---

### Post by nhandler on 2007-03-16
See if ubuntu is detecting the partition by typing:
```
sudo fdisk -l
```

---

### Post by Jormanks on 2007-03-16
> Disco /dev/sda: 163.9 GB, 163928604672 bytes
255 cabezas, 63 sectores/pista, 19929 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1       19929   160079661   42  SFS

Disco /dev/hda: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        3085    24780231    c  W95 FAT32 (LBA)
/dev/hda2            3086        4742    13309852+  83  Linux
/dev/hda3            4743        4998     2056320   82  Linux swap / Solaris

Disco /dev/hdb: 20.0 GB, 20020396032 bytes
255 cabezas, 63 sectores/pista, 2434 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1   *           1        2434    19551073+   7  HPFS/NTFS


Mmmmm..... nope
:(

---

