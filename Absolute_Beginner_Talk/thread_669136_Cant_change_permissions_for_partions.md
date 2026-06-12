---
title: "Cant change permissions for partions"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Nolander on 2008-01-16
ive just repartitioned my hd, but i cant change the permissions on the 2 new partitions. i tried opening nautilus as root but it said u are not the owner so u cant change them. How do i change them and whos the owner?

-nolander

---

### Post by scizzo on 2008-01-16
how does the /etc/fstab mount the partitions?

---

### Post by scizzo on 2008-01-16
also tell us what the command: mount

shows for the partitions

---

### Post by Nolander on 2008-01-16
```
/dev/sda6 on /media/sda6 type vfat (rw)
```
thats what i get from mount but i cant find it in /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8d719d19-1875-43ef-a483-f3c20db070a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=FCA82EA9A82E61FE /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=C4BD-9A20  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=bc15341c-c968-4f8a-a1ee-f8eb1253328c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

i did have sda2(ntfs) and sda5(fat32), i deleted both and made sda5(ext2) and sda6(fat32).

-nolander

---

### Post by scizzo on 2008-01-16
And both of them are mounted at the moment?

What does:

```

ls -l /media/

```

Tell you about the permissions?

PS: Seems like the fstab is wrong according to how the partitioning is being done.

---

### Post by Nolander on 2008-01-16
There both mounted atm and i can change sda5 permissions, but not sda6.

```
drwxrwxrwx 8 nolander   nolander    4096 2008-01-16 20:46 sda5
drwxr-xr-x 3 root       root       16384 1970-01-01 08:00 sda6

```

could it b because its fat32 or is it because fstab is wrong.

-nolander

---

### Post by oodledoodle on 2008-01-16
try the bottom part of this guide, just edit the code to suit your drives.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by scizzo on 2008-01-16
> **oodledoodle said:**
> try the bottom part of this guide, just edit the code to suit your drives.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Yeah follow those instructions. Its a good start to check where it goes wrong. You can also check the files:

```
/var/log/messages
```

```
/var/log/syslog
```

and also

```
dmesg
```

Of how the partitions are being mounted. Also try as a example:

```
umount /media/sda5 && mount -t ext2 -o defaults /dev/sda5 /media/sda5
```

then type:

```
mount && ls -ld /media/sda5
```

and see what the rights for the mount is and see if you can access it ok.

---

