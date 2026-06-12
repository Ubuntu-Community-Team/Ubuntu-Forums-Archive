---
title: "can not access my /home"
date: 2011-02-23
forum: Any Other OS
---

### Post by roger3000 on 2011-02-23
Hi there, 

I am facing an issue with my laptop (Dell precision M4400) where I run Linux Mint KDE 9. 

I have installed this OS with /home on a separate partition.

Since this morning, I can not access this /home partition, even though it appears to be mounted on boot.

Few details:

```
 $ sudo fdisk -l
Disque /dev/sda: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0xa42d04a3

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1               1          41      329301   de  Dell Utility
/dev/sda2   *          42         103      497864   83  Linux
La partition 2 ne se termine pas sur une frontière de cylindre.
/dev/sda3             104       38913   311741231+   5  Etendue
/dev/sda5            2592       37600   281205760   83  Linux
/dev/sda6           37601       38913    10546641   82  Linux swap / Solaris
/dev/sda7             104        2591    19984765+  83  Linux

Les entrées de la table de partitions ne sont pas dans l'ordre du disque
``````
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=83f48a35-ce50-4cce-8a31-637e67eb707e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=d9ec9849-7adb-4b7a-982f-704a475fbcce /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=3849a10c-d9ec-4ad2-b502-a732e59f4ec7 none            swap    sw              0       0
``````
~ $ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2011-02-22 17:01 07DA-041B -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-02-22 17:01 3849a10c-d9ec-4ad2-b502-a732e59f4ec7 -> ../../sda6
lrwxrwxrwx 1 root root 10 2011-02-22 17:01 83f48a35-ce50-4cce-8a31-637e67eb707e -> ../../sda7
lrwxrwxrwx 1 root root 10 2011-02-22 17:01 d9ec9849-7adb-4b7a-982f-704a475fbcce -> ../../sda5
lrwxrwxrwx 1 root root 10 2011-02-22 17:01 f17f2046-3cb2-44c5-84aa-782c05950041 -> ../../sda2
``````

$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07DA-041B" TYPE="vfat" 
/dev/sda2: UUID="f17f2046-3cb2-44c5-84aa-782c05950041" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="data" UUID="d9ec9849-7adb-4b7a-982f-704a475fbcce" TYPE="ext4" 
/dev/sda6: UUID="3849a10c-d9ec-4ad2-b502-a732e59f4ec7" TYPE="swap" 
/dev/sda7: UUID="83f48a35-ce50-4cce-8a31-637e67eb707e" TYPE="ext4"
``````
$ sudo mount
[sudo] password for manu: 
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```> sudo mount -agives no reply. 

I tried installing disk manager, following these links (in french...):
[doc.ubuntu-fr.org/disk-manager]("http://doc.ubuntu-fr.org/disk-manager") ; [doc.ubuntu-fr.org/tutoriel/deplacer_home...edure_tres_commentee]("http://doc.ubuntu-fr.org/tutoriel/deplacer_home#procedure_tres_commentee"),
but I did not succeed in starting it...

I would greatly appreciate your help!!

thanks a lot!

---

### Post by nothingspecial on 2011-02-23
First glance, why has your /home, /dev/sda5, got a label "data"?

That could be the problem although I'm honestly not sure.

---

### Post by roger3000 on 2011-02-23
well, I gave this partition a label "data" during the install... no reason why :)

To be sure, I just removed this label, but it did not change anything...

---

### Post by roger3000 on 2011-02-23
well, it appeared to be a problem of permissions: reverting the /home folder's permissions from 'root' to 'my login' fixed the issue...

don't know why it changed, though...

---

