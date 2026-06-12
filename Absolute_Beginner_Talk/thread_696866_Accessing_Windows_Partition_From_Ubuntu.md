---
title: "Accessing Windows Partition From Ubuntu"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-02-14
At the moment I've got a windows partition and a ubuntu partition on my laptop.  When I try to access my windows partition, though, it tells me that the device can not be mounted.  How can I force this to mount so I can view my windows files?

---

### Post by Crooksey on 2008-02-14
Are you mounting the hard-drive from boot with an fstab entry, or though HAL?

---

### Post by jan quark on 2008-02-14
please post the output of these terminal commands

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

also make sure you have shutdown windows properly not only hibernated or such things

---

### Post by LRT on 2008-02-14
i used this when i still cared about my windows partition... 

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

this will allow you to mount, read and write to your windows partition

---

### Post by jordank on 2008-02-14
yeah here's the problem.  My windows partition was not shut down properly. It's "broken" at the moment, and i'm just trying to recover one file from it.  I don't know how I can mount it.

---

### Post by jan quark on 2008-02-14
hey not bad just a guess with this not shutdown properly

well you cannot go back to windows and ... no that would be too easy

please post the results of the terminal commands posted above

thank you

---

### Post by jordank on 2008-02-15
jordan@Jorcomp:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/PASSPORT type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=jordan)
jordan@Jorcomp:~$ sudo fdisk -l
[sudo] password for jordan:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc25a6858

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9352    75119908+  83  Linux
/dev/sda2   *        9353       18705    75126784    7  HPFS/NTFS
/dev/sda3           18706       19457     6040440    5  Extended
/dev/sda5           18706       19457     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab426633

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS
jordan@Jorcomp:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=952eab43-54e9-4890-8a40-b7909b6a0715 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8e144033-8ee5-4d84-b3ea-f1ddadf00c51 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
jordan@Jorcomp:~$

---

