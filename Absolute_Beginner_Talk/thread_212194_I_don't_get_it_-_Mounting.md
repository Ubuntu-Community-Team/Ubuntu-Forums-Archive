---
title: "I don't get it - Mounting"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by roxics on 2006-07-09
Last time I installed ubuntu on this same system (5 days ago) all my hard drives (I have foiur of them) were mounted and avialable for reading on my desktop. Now none of them are. I go into pl;aces>computer and they are all there but when I right click on one of them at the very bottom it says "Unmount Volume" but there is nothing mounted on my desktop and double clicking on the drives icon doesn't result in anything happening. It doesn't open or anything.

---

### Post by taurus on 2006-07-09
What is the output of this command from a terminal (Applications -> Accessories -> Terminal)?
```

more /etc/fstab

```

---

### Post by roxics on 2006-07-09
I get this

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0



After restarting my system it now says "mount" rather then "unmount volume" when right clickng on a drive icon. Whne I try to mount it tells me I can't.

---

### Post by taurus on 2006-07-09
Looks like you only have /dev/hde1 (root) mount at this point!!!  Are all the partitions in /dev/hde?  What is the output of this command from a terminal again and which partition do you want to mount where?
```

sudo fdisk -l

```

---

### Post by roxics on 2006-07-09
This is what I get.

> 
Disk /dev/hde: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        2330    18715693+  83  Linux
/dev/hde2            2331        2434      835380    5  Extended
/dev/hde5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/hdg: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19457   156288321    7  HPFS/NTFS




I have four hard drives.
20gig - Ubuntu EXT3
60gig - Windows XP NTFS
120gig - Videos and other media NTFS
160gig - Photos and Video NTFS

I'd like to read all three of my other drives from within ubuntu

---

### Post by aysiu on 2006-07-09
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by roxics on 2006-07-10
Ok, following the instructions from that link (thanks for the link) i had a bit of a hard time understanding them but I edited my fstab file into this:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdg1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hdc1       /windows        ntfs    nls=utf8,umask=0222        0       0


I then remounted and rebooted my system. Upon reboot my 160gig drive is accessible but my 60gig and 120gig still are not. When I right click on them and try to mount them I get this message:

> 
mount: according to mtab, /dev/hdg1 is already mounted on /windows

mount failed


On a side note, I really like how every information window can be highlighted and copied unlike in Windows. Makes it so much easier to show you guys whats going on.

---

### Post by trackerd on 2006-07-10
when I think of mounting... its not a pg visual :)

---

### Post by digby on 2006-07-10
> **roxics said:**
> I then remounted and rebooted my system. Upon reboot my 160gig drive is accessible but my 60gig and 120gig still are not. When I right click on them and try to mount them I get this message:
In your /etc/fstab, you have this:```
 
/dev/hdg1       **[B]/windows**[/B]        ntfs    nls=utf8,umask=0222        0       0
/dev/hda1       **[B]/windows**[/B]        ntfs    nls=utf8,umask=0222        0       0
/dev/hdc1       **[B]/windows**[/B]        ntfs    nls=utf8,umask=0222        0       0
```The problem is that you are trying to mount all three partitions to the same folder.  The way linux deals with extra partitions (hard drives, removable media, etc.) is to place them as if they were just another branch in the file system.  You're basically trying to grow three branches in the same place.  If you change that to something like```

/dev/hdg1       **[B]/media/windows**[/B]        ntfs    nls=utf8,umask=0222        0       0
/dev/hda1       **[B]/media/pics**[/B]           ntfs    nls=utf8,umask=0222        0       0
/dev/hdc1       **[B]/media/video**[/B]          ntfs    nls=utf8,umask=0222        0       0
``` It should work.

As a side note, you will have to make those extra directories:```
sudo mkdir /media/windows
```... and so on...

edit: attempting to fix spacing...

---

### Post by jonrkc on 2006-07-10
What happens if you unmount (as root) hdg1 and then remount it, manually, like this...
```

umount /windows
mount -t ntfs /dev/hdg1 /windows

```
That might give a clue as to what's going on...I think.

**Edit:**I posted this right as Digby was posting the one above it.  So you may want to just disrgard this one.

---

### Post by roxics on 2006-07-10
Thank you digby. That worked out great. After editing and a reboot of my system all three of those other drives now show up on my desktop and I can get to them all. 

Thank you everybody for all your help. :)

---

### Post by digby on 2006-07-10
If you have to make changes to /etc/fstab again, you don't really need to reboot to mount everything.  You can just run ```
sudo mount -a
```Glad to hear it worked for you.  Enjoy!

---

