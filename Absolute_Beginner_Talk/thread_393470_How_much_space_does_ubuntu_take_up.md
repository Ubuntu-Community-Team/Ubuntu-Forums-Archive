---
title: "How much space does ubuntu take up?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Oddjob74 on 2007-03-25
I have recently installed ubuntu on my laptop! My hard drive is supposedly 100gig. But when I look at the disc on ubuntu it says its 93gig and has only 82gig free! Inoticed that there is a partion of 2 and a bit gig for what I would presume is the ubuntu operating system! So where has the rest gone!? Ubuntu is the only OS on the laptop!

---

### Post by dacool25 on 2007-03-25
Linux also has to use a swap drive, it may be to that, however those are usually small.  If you would like to view all of your partitions go to terminal > and type in sudo fdisk -l

that will show you all of your current partitions, good luck.

---

### Post by ThrobbingBrain66 on 2007-03-25
A default Ubuntu install should only takes up about 2.5 gigs.  Could you please post the output of ```
 cat /etc/fstab
```

This will show us what partitions are on your hard disk

---

### Post by Oddjob74 on 2007-03-25
> **ThrobbingBrain66 said:**
> A default Ubuntu install should only takes up about 2.5 gigs.  Could you please post the output of ```
 cat /etc/fstab
```

This will show us what partitions are on your hard disk

I am a complete neewbie to ubuntu. So how do I enter the code! :confused:

Also I have been trying to find where the 'terminal' is (which dacool25 suggested). How do I find that! Maybe I should of read up abit on Ubuntu before jumping in at the deep end!! Heard so many good thigs about it tho!

---

### Post by jerryrw on 2007-03-25
Go to Applications->Terminal to get to a term to enter commands.

Additionally try a:

sudo df -h

This will tell you where your disk usage is at.

---

### Post by tonyr1988 on 2007-03-25
> **jerryrw said:**
> Go to Applications->Terminal to get to a term to enter commands.

Additionally try a:

sudo df -h

This will tell you where your disk usage is at.
Not a biggie, but just in case:

It's Applications -> Accessories -> Terminal

---

### Post by Oddjob74 on 2007-03-25
Well here are the £ suggested code results! Means nothing to me really! Make sense to anyone else?



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0



Filesystem            Size Used Avail Use% Mounted on
/dev/hda1              89G  1.9G   83G   3% /
varrun                502M   84K  502M   1% /var/run
varlock               502M  4.0K  502M   1% /var/lock
udev                  502M  132K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   19M  483M   4% /lib/modules/2.6.15-26-386/volatile


Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11787    94679046   83  Linux
/dev/hda2           11788       12161     3004155    5  Extended
/dev/hda5           11788       12161     3004123+  82  Linux swap / Solaris

---

### Post by ThrobbingBrain66 on 2007-03-25
Normally, a "100GB" hard drive has only about 93GB of usable space, so that accounts for 7GB.  But your partitions looked messed up. The output of df -h for dev/hda1 doesn't make sense.  Someone with more experience with partitioning will have to step in.

Good luck!

---

