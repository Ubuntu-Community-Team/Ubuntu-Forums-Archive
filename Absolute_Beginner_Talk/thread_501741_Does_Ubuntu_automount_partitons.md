---
title: "Does Ubuntu automount partitons?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Lolicon on 2007-07-15
I was using Linuxmint on my computer, and it never automounted my partitons. I think I'll dump it if Ubuntu automounts partitions (Linuxmint automounted NTFS but never EXT2). Does it, or do I still need to fail at editing fstab? :)

---

### Post by freebird54 on 2007-07-15
Well - you could try SUCCEEDING at editing fstab!  Lots of people here can help with that.  It'll even STAY fixed if you use the UUID methods of mounting.

Just post a

```
sudo fdisk -l
```

and a 

```
cat /etc/fstab
```

to see what we can come up with for you.. :)

---

### Post by Lolicon on 2007-07-15
Ah ok. I just reinstalled windows so now my booting order is gone. I'm going to fix again soon I guess...
I'll just open it in textpad...
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8b588b96-917d-4b49-8357-316281e95984 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda9
UUID=c0f3b1dd-4de8-4a96-8609-4325b5a96887 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda5 /media/f              ext2	auto,user,exec,rw 0       0

/dev/sda6 /media/d              ext2	auto,user,exec,rw 0       0

/dev/sda7 /media/g              ext2	auto,user,exec,rw 0       0


As you can tell the
> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda5 /media/f              ext2	auto,user,exec,rw 0       0

/dev/sda6 /media/d              ext2	auto,user,exec,rw 0       0

/dev/sda7 /media/g              ext2	auto,user,exec,rw 0       0
was made by me.

---

### Post by freebird54 on 2007-07-15
And those entries by you are what exactly (or SUPPOSED to be what exactly?)

Just wondering why they are ext2 formatted ....

can you post the output of

```
sudo fdisk -l
```

and/or tell me what the others are supposed to be?

---

### Post by Lolicon on 2007-07-15
ah, im on windows right now. After I reinstalled it I had problems with logging back into linuxmint. Can you tell me how to reinstate my boot to GRUB?

---

### Post by Lolicon on 2007-07-15
Does anyone know if Ubuntu automount partitons?

---

### Post by Nythain on 2007-07-15
its linux... it will automount whats contained in the fstab
you can tell it where you want to mount what partitions during the installation of ubuntu so you never have to mess with the fstab, it will take care of it for you.
just select the partition, and pick manually enter mount point, or whatever its called... then tell it where you want it to mount...
like i have two large hard drives for storage
one i mount at /data
and teh other at /data/video
so during the installation of ubuntu, when i get to the partitioning phase, i select what is sdb1 on my machine (thats my first storage drive), tell it NOT to format the partition, then manually set its mount point to /data
then i select sdc1, tell it NOT to format the partition, and manaully set its mount to /data/video
then the installation takes care of setting up the fstab, gets the correct uuid for the drive, in case its device name or label actually change, and all is groovy

post installation manual editing of fstab is simple as can be really... if you need any help many of us here can get you going with that

edit: if you would like to use uuid instead of device you can obtain the uuid of all partitions, and any labels they have by opening up terminal and typing blkid

---

### Post by freebird54 on 2007-07-15
If you can't get back in because of Grub problems, [this](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD) is a way to get it back from an Ubuntu Live CD.

---

