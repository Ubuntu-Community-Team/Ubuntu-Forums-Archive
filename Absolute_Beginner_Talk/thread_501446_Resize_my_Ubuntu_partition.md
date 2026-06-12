---
title: "Resize my Ubuntu partition"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Bob Bismal on 2007-07-15
Another freakin' newbie here.  Complete newbie.  I've been reading some startup guides but still very new.  Anyways, I'm dual booting Vista and Ubuntu 7.04.  1.73Ghz Celeron 1406MB RAM ATI video.  I used Vista to make a 3GB partition to install Ubuntu on.  Yea... turns out I need more.  Is there a way either through Vista or Ubuntu to make my 3GB partition bigger?

On a side note, while setting up Ubuntu it made another small (like 196mb) partition.  Is that normal?  I thought it would install everything in the 3GB partition I made.  

I'm not totally against starting over from scratch, but I'd really rather not.  Now that I have a dual boot system, and my start up uses gnome, is everything going to go crazy it I just delete my Ubuntu partition to start over?  A lot of questions, thanks for your help.

I've heard ATI cards can cause problems.  How do I know if my ATI card is working correctly or not?

---

### Post by mytwobears on 2007-07-15
You can use gparted, which is on the live CD, to make the disk larger.  The 256MB is probably for the swap partition.  Ubuntu usually needs at least 2 partitions.  One swap partition and one / (root) partition.  Your swap partition should be twice the the amount of ram on your computer.

Just boot from the Live CD, then choose gparted, the partition program, and use it to make your linux partition larger.  You should really allow Ubuntu 10GB, definitely more than 3 or 5GB.

HTH :).

---

### Post by bapoumba on 2007-07-15
Thread moved to the "Absolute Beginner Talk" support forum.

---

### Post by Bob Bismal on 2007-07-15
Should I use Vista partition thingy to alocate more free space before I start messing with that?

---

### Post by ron999 on 2007-07-15
> **Bob Bismal said:**
> Should I use Vista partition thingy to alocate more free space before I start messing with that?
No, use the LiveCD as mytwobears has said.
It's not called gParted in the menu, it is Gnome Partition Manager.

---

### Post by Bob Bismal on 2007-07-15
Tried the Gnome Partition Manager  it would let me make the partitions smaller but not bigger.  And it wouldn't even give me the option to change the size of the swap partition.  Help?

---

### Post by Bob Bismal on 2007-07-15
Any way to make the partitions bigger?  Or is there something I'm missing in Gnome partition Manager?

---

### Post by anarchyreigns on 2007-07-15
Did you boot to the LIveCD or did you just try and run it from within your operating system. You can't resize a partition you are using, so you'll need to "boot" to the LiveCD.

---

