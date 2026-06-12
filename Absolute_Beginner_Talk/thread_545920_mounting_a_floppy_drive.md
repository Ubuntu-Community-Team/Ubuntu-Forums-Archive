---
title: "mounting a floppy drive"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by goofy328 on 2007-09-08
When I try to mount a floppy drive it tells me 

unable to mount volume

mount: /dev/fd0 is not a valid block device

---

### Post by alienexplorers on 2007-09-08
Try this:
> /dev/fd0        /media/floppy   vfat    rw,user,noauto  0       0
put this in your fstab file and you will not have to mount the drive each time you use it.

---

### Post by goofy328 on 2007-09-08
Do I replace 

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

with 

/dev/fd0 /media/floppy vfat rw,user,noauto 0 0

or add it to it?

---

### Post by philinux on 2007-09-08
> **goofy328 said:**
> When I try to mount a floppy drive it tells me 

unable to mount volume

mount: /dev/fd0 is not a valid block device

You only get that error if there is no disk in the drive. :lolflag:

If you have'nt got it installed get Kfloppy from synaptic its a great gui for floppys.

---

### Post by alienexplorers on 2007-09-08
If you already have it in your fstab then the floppy should automount when you insert and read or write to the floppy.

---

### Post by goofy328 on 2007-09-08
I do have a disk in the drive and I do not want to reformat the drive because I have data on it, though I did install Kflopy.  I added the line to my fstab but it still isn't working.

---

### Post by alienexplorers on 2007-09-08
Did you try another floppy in the drive.  In the mount directory what name do you have in there for the floppy.  If you used my mount line in your fstab it should read /media/floppy.

---

### Post by philinux on 2007-09-08
Alien is dead right sounds like your floppy bit the dust. :(
Is there a utility for recovering data from it?

---

### Post by goofy328 on 2007-09-08
I don't know how I got the sh* to work but it finally went through.  Now I just have to get a decent floppy because the one I was working with had errors on it.  Thanks!

---

