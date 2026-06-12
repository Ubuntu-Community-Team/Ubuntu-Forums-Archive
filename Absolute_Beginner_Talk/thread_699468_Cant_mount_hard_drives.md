---
title: "Cant mount hard drives"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-02-17
I have  parttions on my PC; 1 which is ''fliesystem'' where ubuntu is installed, and the other two were visible and than one day they just dissapeared!!??how can I remount them??

---

### Post by sb12 on 2008-02-17
> **munch3 said:**
> I have  parttions on my PC; 1 which is ''fliesystem'' where ubuntu is installed, and the other two were visible and than one day they just dissapeared!!??how can I remount them??

sudo mount /dev/whatever

---

### Post by munch3 on 2008-02-17
and ''whatever'' would be... remember dude, ur in absolute beginner section ^^

---

### Post by sb12 on 2008-02-17
ok first paste the output of fdisk -l

---

### Post by jan quark on 2008-02-17
post the output from

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

then we will see

---

### Post by munch3 on 2008-02-17
> /dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)


> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2545f9d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        5349     2008125   82  Linux swap / Solaris
/dev/sda3            5350       19457   113322510   83  Linux

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30b9c739

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=42db8128-8dd4-4dd8-a96b-701abfcbe108 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=6274C7D674C7AADD /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=0E54A3B054A3994B /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=8c9989b6-0f38-46e8-b7cb-aa0901578abc none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
 .I dunno hw to put terminal codes wrapped like that so im quoting ^^

---

### Post by sb12 on 2008-02-17
try typing sudo mount -a

---

### Post by jan quark on 2008-02-17
check this first

go to places > computer > filesystem > media
and see if you can access hda1 and sda1

---

### Post by munch3 on 2008-02-17
well look at that, they just reappeared again when i restarted the system ... nvm tnx for the help

---

### Post by Northsider on 2008-02-17
> **munch3 said:**
> well look at that, they just reappeared again when i restarted the system ... nvm tnx for the help

Sometimes that happens with me too.  When mounting and external hard drives are giving me problems, I reboot and "magically" it appears and I can use it.:)

---

