---
title: "[SOLVED] partition problem"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Abu Noor-Eddin on 2008-04-19
Hi all, 

I am new to Ubuntu. I am using Ubuntu 7.04 on my Hp 530 notebook. Everything is running great. 

I have two Windows partitions (FAT32) and I can access them for Ubuntu. I divided the rest of my hard desk into three partitions (ext3) (the first one is the root, the second one is the swap partition, and the third one I let it to save all my data on it). 

When I want to cppy any thing on this third partition /media/sda8 I found the paste is not active. Besides I cannot move anything to this partition. 

The create folder and create document are also not active. The only active thing when I right click the partition is "unmount". 

I think that there is something wrong. I am waiting for your help.

Thanks in advance.

---

### Post by bodhi.zazen on 2008-04-19
All you need do is configure the mount. This involves first unmounting the partitions and then editing /etc/fstab and finally re-mounting them.

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

---

### Post by Abu Noor-Eddin on 2008-04-19
> **bodhi.zazen said:**
> All you need do is configure the mount. This involves first unmounting the partitions and then editing /etc/fstab and finally re-mounting them.

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

The problem is not in the Windows partitions but it is in the Linux partitions !!

---

### Post by annda on 2008-04-19
it looks like sda8 is mounted as read-only

please post the contents of your /etc/fstab file (or are you mounting the partition manually?)

---

### Post by Abu Noor-Eddin on 2008-04-19
Here is the content of my fstab file

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0cb89b74-f1d9-419c-871f-f6f012715d65 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3B55-15FD  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=2E3B-1B0F  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=a63d7ed5-35d5-4cf5-bc83-9dd7f9384e17 /media/sda8     ext3    defaults        0       2
# /dev/sda7
UUID=9e314ecc-206b-401c-8199-0f0ac3193213 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


```

---

### Post by bodhi.zazen on 2008-04-19
oops :redface:

For linux partitions, first mount the device

```
sudo chown user.users /media/sda8
sudo chmod 770 /media/sda8
```

where user = your user name

see also the link I gave you on fstab.

---

### Post by Abu Noor-Eddin on 2008-04-19
> **bodhi.zazen said:**
> 
```
sudo chown user.users /media/sda8
sudo chmod 770 /media/sda8
```


Thanks. It works after relogin.

---

### Post by annda on 2008-04-19
DELETED because it is redundant (too late again)

---

