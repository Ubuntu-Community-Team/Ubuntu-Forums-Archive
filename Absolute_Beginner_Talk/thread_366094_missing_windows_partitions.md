---
title: "missing windows partitions"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by steveandarchie on 2007-02-20
Hello

I have installed edgy intending to dual boot with winXP but XP will not boot. That's no big problem as I'll eventually take it off but before that I need to burn some data from the XP partition. 

My other installation of Ubuntu mounts the windows partitions automatically at start up but this one doesn't and a look at 'Computer' in 'Places' doesn't show the partition - only the CDROM and filesystem. Gnome Commander doesn't seem to see it either but a live boot with slax/kanotix/puppy all reveal the missing XP partition - the problem being (apart from Puppy) that I need the CD to burn the data.

Here's the fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda3
UUID=d72418b9-dfad-465a-9bbc-c36b46c6cf7b / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=5b123f72-4a21-4649-823e-e63ac0f7674e none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0 

And here's sudo fdisk -l:

> Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2343    18820116    c  W95 FAT32 (LBA)
/dev/hda2            2344        2851     4080510    c  W95 FAT32 (LBA)
/dev/hda3            2852        3611     6104700   83  Linux
/dev/hda4            3612        3648      297202+   5  Extended
/dev/hda5            3612        3648      297171   82  Linux swap / Solaris

I tried the instructions here: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) but no joy - the fstab amendments are not very well explained. Any ideas?

Many thanks

---

### Post by taurus on 2007-02-20
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```

/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
/dev/hda2   /media/hda2   vfat   iocharset=utf8,umask=000   0   0

```
Save it.  Now, create two new mount points and mount them.

```
sudo mkdir /media/hda1 /media/hda2
sudo mount -a
df -h
```

---

### Post by steveandarchie on 2007-02-20
:lolflag: 

Fantastic - worked a treat. You wouldn't believe how many threads I trawled through before asking. Still, I picked some useful stuff up on the way.

Thank you very much for your help taurus.

Hey - just spotted your location. I spent some good times in and around Jacksonville - especially the sports bar outside Lejeune camp (I was British RM)

---

### Post by taurus on 2007-02-20
You're welcome and have fun.

---

