---
title: "Write to NTFS HD"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by nhandler on 2006-12-17
I am trying to write to an external hard drive I have in Ubuntu (Edgy Eft). I am able to read it fine, I just can't write to it. I know write support isn't working 100% yet, but I really need to be able to write to it. I've followed a lot of tutorials, and they all result in the drive a) not mounting or b) mounting as read only. Could someone please help me out? Thanks.

---

### Post by taurus on 2006-12-17
Here you go...

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by milad on 2006-12-17
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

### Post by milad on 2006-12-17
Take a look at here:
It worked for me

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

### Post by bodhi.zazen on 2006-12-17
The above links should do the trick.

If not please post

```
sudo fdisk -l
```

and the contents of /etc/fstab

---

### Post by nhandler on 2006-12-17
> **taurus said:**
> Here you go...

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

I tried that. It says
mount: only root can mount /dev/sdb1 on /media/external

when I try to open up the drive in the file browser. I posted in the other thread as well, so you don't need to reply here. I'm just letting you know.

---

### Post by taurus on 2006-12-17
Put the sudo in front of the mount command if you want to mount it by hand...

---

### Post by nhandler on 2006-12-17
Is there any way to do it automatically?

---

### Post by taurus on 2006-12-17
Yes, through /etc/fstab.  So, what's the output of this command and the content of your /etc/fstab...

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by nhandler on 2006-12-17
> **taurus said:**
> Yes, through /etc/fstab.  So, what's the output of this command and the content of your /etc/fstab...

```
sudo fdisk -l
cat /etc/fstab
```

> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7111    57119076   83  Linux
/dev/sda2            7112        7296     1486012+   5  Extended
/dev/sda5            7112        7296     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300001443328 bytes
255 heads, 63 sectors/track, 36473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36472   292961308+   7  HPFS/NTFS


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=e01e3ea2-5d19-4afc-addd-0cf5d6477eb9 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=212c7663-87c8-469b-b332-4c5da5aafd53 none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /media/External ntfs-3g defaults.locale=en_US.utf8      0       0


Those are the outputs from the two commands.

---

### Post by bodhi.zazen on 2006-12-17
Change the fstab entry to:

> /dev/sdb1 /media/External ntfs-3g **auto**,locale=en_US.utf8 0 0

and it should now mount at boot :p

---

