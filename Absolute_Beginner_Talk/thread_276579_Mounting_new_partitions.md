---
title: "Mounting new partitions"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by happybill on 2006-10-13
If this topic is already covered in earlier threads, I'm sorry, but I haven't found any.

I'm trying out Ubuntu 6.06 alongside XP.  In XP I keep a separate partition for my data, including the data store for Outlook Express 6.  I want to have a similar facility in Ubuntu.  Having found that it is possible to read from, write to, and save files in a FAT32 partition while running Ubuntu, I used gparted to make two new logical partitions for my data on the second hard drive; they are hdb9 and hdb10.  Try as I may by editing fstab and using mount, I cannot mount them so they are useless at present.  All my actions merely imitate what I have found in the posts, because I do not really understand what needs to be done.

Any advice will be very welcome.

---

### Post by gontofe on 2006-10-13
try creating the mount points:

sudo mkdir /media/disk1
sudo mkdir /media/disk2

then try mounting

sudo mount /dev/hdb9 /media/disk1
sudo mount /dev/hdb10 /media/disk2

get this bit sorted, then worry about the fstab entries once you get them mounted manually.

---

### Post by happybill on 2006-10-13
Many thanks.

I did as suggested, and the partitions are now mounted.  I know this from gparted and from messages when I tried to mount them. Is this topic written up anywhere?

There is still a problem.  The new partitions are not visible on the desktop, nor are they listed under Computer. How can I make them visible and useful?

---

### Post by Kateikyoushi on 2006-10-13
You can check them by going to the /media/disk1, 2 folders.

If the partitions are mounted fine add them to the fstab.

First backup then edit fstab.

```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

Add these lines to the end and save it.

```
/dev/hdb9    /media/disk1 vfat  iocharset=utf8,umask=000  0    0
/dev/hdb10    /media/disk2 vfat  iocharset=utf8,umask=000  0    0
```

---

### Post by happybill on 2006-10-13
Thank you, Kateikyoushi.

I tried what you suggest and ended up with two new partitions called disk1 and disk2.  From the original contents of fstab, I had assumed that the new partitions would show up as hdb9 and hdb10, as in gparted. Please note that hdb9 is formatted as ext3 and hdb10 is FAT32.  I altered part of your code for hdb9 to be the same as for my other ext3 partition.  Why did it work using disk1 etc and not hdb9 etc?  I feel uneasy with a partitions called disk1 and disk2 in Computer and hdb9 and hdb10 in gparted - should I?

For what it is worth, the contents of fstab, before the change was attempted, were

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda10      /media/hda10    vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda11      /media/hda11    vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7       /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda8       /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda9       /media/hda9     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb5       /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb6       /media/hdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb7       /media/hdb7     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb8       /media/hdb8     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

