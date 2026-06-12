---
title: "resizing dual boot partition -xp"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by thepopasmurf on 2007-08-09
When I installed Ubuntu, I gave too much space to ubuntu not enough to xp, what would be the best way to fix this

---

### Post by alienexplorers on 2007-08-09
You would need to run gparted to resize the partitions.  Make sure you run defrag from windows several times before doing the resize.

---

### Post by thepopasmurf on 2007-08-09
I'm trying to resize my partitions to give more memory to XP.
I'm using GParted to do it but I ran into a problem, I reduced the size of the ubuntu 
partition but I can't give the unallocated to xp, how do I do this.

[IMG]http://image.bayimg.com/eafjhaabh.jpg[/IMG]

Here is a picture I drew which I hope highlights the main details which I got from
GParted.

*The /dev/sda2 is XP (I think)
*The /dev/sda6 is Ubuntu (I think)

The blue section is called "extended", I don't know what to do with it

---

### Post by logos34 on 2007-08-09
The extended partition contains ubuntu (logical partition).  Windows is a primary partition.  Can't you shrink/resize the extended parition (sda3?) by dragging the slider to the right?

---

### Post by thepopasmurf on 2007-08-09
I think I already tried that, I might try it again soon, but I am not able to do anything to the unallocated part

---

### Post by AlexenderReez on 2007-08-09
> **thepopasmurf said:**
> I'm trying to resize my partitions to give more memory to XP.
I'm using GParted to do it but I ran into a problem, I reduced the size of the ubuntu 
partition but I can't give the unallocated to xp, how do I do this.

[IMG]http://image.bayimg.com/eafjhaabh.jpg[/IMG]

Here is a picture I drew which I hope highlights the main details which I got from
GParted.

*The /dev/sda2 is XP (I think)
*The /dev/sda6 is Ubuntu (I think)

The blue section is called "extended", I don't know what to do with it

you have unused partition 60g...why don't use it?

---

### Post by MenZa on 2007-08-09
I don't think I'd play too much with NTFS partitions (especially with Windows installed) in gparted...

---

### Post by logos34 on 2007-08-09
if you can't shrink the extended, why don't you just turn part or all of the unallocated 62 gig space into a ntfs or ext3 data partition, then get the appropriate drivers so each OS can read+write to it (fs-driver for windows and ntfs-3g for linux).  that's the easiest solution

---

