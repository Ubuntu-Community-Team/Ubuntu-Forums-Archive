---
title: "[SOLVED] drive permissions"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by colddayinapril on 2007-07-16
i just formated my western digital external drive into ext3, but i have a series of problems:

it shows up in the system monitor as being 458 gigs (not the 500 it should be) and as using the ext3 file system.

heres what shows up when i use fdisk -l:

```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   c  W95 FAT32 (LBA)
```

so, not only am i missing about 35 gigs, apparently, the system thinls the drive is still in FAT32!

also, i tried hooking the drive upto a Windows box (just for the f$#k of it) and it reads it as unformated, but only at 465 gigs. 

when using gparted, it shows up as formated for ext3, but with a size of 465.

i have no idea what to do here... i'm not even sure what my problem is, let alone hwo to fix it.
i've been all over google, and i'm at a total loss. :confused:


if it helps,  this is a link to the how to i used to format the drive:
[http://www.ehow.com/how_1000631_hard-drive-linux.html](http://www.ehow.com/how_1000631_hard-drive-linux.html)

I followed the instructions to the letter, except i used ext3 instead of ext2.


any ideas guys?

---

### Post by aysiu on 2007-07-16
Forget about the gig stuff. Gigs can be measured in a myriad of ways, so the numbers won't always be the same. Read more here:
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

I don't know what's going on with the FAT32/Ext3 confusion. Try this instead of the eHow tutorial:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by colddayinapril on 2007-07-16
ok, i did some more digging and found out about the GB thing myself... disapointing to say the least, but i suppose it's better than having an f'd up drive :)

as to the guide you posted, it worked... sort of.
the drive now has a name, and is mounted, and i have permmision to write to it.
however, fdisk is still saying the same thing as before.

....let me try rebooting. see if that makes any difference

brb *fingers crossed*

---

### Post by colddayinapril on 2007-07-16
ok, no luck with rebooting...
still says the same thing.

---

### Post by colddayinapril on 2007-07-16
-update-

been pokin' around a bit (don't hold your breath... i did'tn actualy *DO* anything :D )

heres what i got:

sudo fdisk -l :
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   c  W95 FAT32 (LBA
```)


sudo fdisk /dev/sdb1
```
Disk /dev/sdb1: 500.0 GB, 500096991744 bytes
255 heads, 63 sectors/track, 60799 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1       60799   488367936   83  Linux
```


so umm... yeah
to put this proper terms, somethings f'd up here :confused:

---

### Post by colddayinapril on 2007-07-16
ok, got it fixed.

i deleted both partitions using gparted and reformated.
everythings looking right now.

i guess my command line skills need work.. i probably screwed it up while formatting using fdisk.


thanks guys.

---

