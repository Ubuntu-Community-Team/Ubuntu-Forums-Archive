---
title: "Move /home/ to a separate drive"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-12-07
I am just about to install a new drive.  I want to leave the operating system where it is but to move the  /home directory to the new drive.  I am planning to do this by editing fstab and then copying over the present contents of /home.

My existing fstab is this 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=21941f18-a2f7-423e-8009-d10bbd332be5 /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
# /dev/hda5
UUID=349a4bbd-cff3-4fb1-818a-ebd48c546c21 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
and I am planning to change it to this
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=21941f18-a2f7-423e-8009-d10bbd332be5 /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
/dev/hda1/home	/media/sda1/home/		 ext3    defaults	0	2
# /dev/hda5
UUID=349a4bbd-cff3-4fb1-818a-ebd48c546c21 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

#/dev/sda1
/dev/sda1	/media/sda1/home/			ext3	defaults		0	2

```

Have I overlooked anything here?

---

### Post by philinux on 2007-12-07
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I used this guide, some of it needs a slight update.

---

### Post by logos34 on 2007-12-07
> **expatCM said:**
> 
#/dev/sda1
/dev/sda1	/media/sda1/home/			ext3	defaults		0	2
[/CODE]

Have I overlooked anything here?


fstab needs to look like this:
> #/dev/sda1
/dev/sda1	/home			ext3	defaults		0	2

---

### Post by expatCM on 2007-12-07
Thank you both for your comments ...

philinux - I had a look at the link but it seems to be a bit like partitioning an existing volume.  What I need to know is whether I have made a mess in fstab since that always means finding the Live CD..

logos34 - thank you for pointing out what I should have on sda1

Did I get this line right?
/dev/hda1/home	/media/sda1/home/		 ext3    defaults	0	2

---

### Post by banewman on 2007-12-07
/dev/hda1 is what you want to mount
/home is where you want to mount it - so 
/dev/hda1 /home ext3 defaults 2 0 
:)

---

### Post by lamalex on 2007-12-07
You  may also want to put the disk in fstab by UUID and not dev address, like the other disks. To get the uuid execute this..
```
ls -lah /dev/disk/by-uuid/
```

---

### Post by expatCM on 2007-12-07
banewman - sorry but I just got lost ...

the default drive is hda1 where the operating system is installed.

The new drive where I want /home to be is sda1.

So if I do not have an entry in hda1 telling the system that /home has moved to sda1 then will it not simply use the old location?

---

### Post by expatCM on 2007-12-07
lamalex - very cool ... that helps keep everything consistent, thank you.

---

### Post by Wilfred on 2007-12-07
I have used this tutorial (on 7.04) which worked fine in my case after I bought a new harddisk for /home

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Good luck!

---

