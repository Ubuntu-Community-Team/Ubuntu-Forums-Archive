---
title: "Bootable Live CD for partitioning (on iMac)"
date: 2007-09-17
forum: Apple PPC Users
---

### Post by Average_Joe on 2007-09-17
I'm preparing to install Ubuntu 7.04 or Ubuntu 6.06 or Ubuntu 6.10 (can't decide which, yet) onto a
iMac PowerPC G3 500 Mhz.

But first, I need a bootable Live CD which contains a good partitioner so that I can shrink the existing OS X partition.

I've read the very nice help sections here and don't see any mentioned.

What is a good bootable Live CD partitioning editor that will boot onto a PPC iMac?

Thanks all!

---

### Post by Auria on 2007-09-17
Ubuntu has a LiveCD for ppc. You will find download links along the FAQ in the sticky at the top of this forum section

good luck (BTW: if you cant decide, try 7.04... it has lots of ppc fixes the others dont)

---

### Post by pxwpxw on 2007-09-17
As above, and also, it may be possible to shrink the macosx partition using the macosx "diskutil" resizeVolume teminal command (in macosx 10.4.6 or higher).

---

### Post by Average_Joe on 2007-09-18
Thanks for the replies.  I'm aware of the PPC Live CD for Ubuntu.  However, does that Live CD contain a good partitioner for Mac formatted hard drives?

I guess I am asking if the ever-popular GParted will resize OS X partitions.
Thanks again.

---

### Post by pxwpxw on 2007-09-18
> **Average_Joe said:**
> Thanks for the replies.  I'm aware of the PPC Live CD for Ubuntu.  However, does that Live CD contain a good partitioner for Mac formatted hard drives?

I guess I am asking if the ever-popular GParted will resize OS X partitions.
Thanks again.

Well I did use live cd gparted (or parted for command line) to resize the Macosx HFS+ partition on a Mac Intel (macbook), just to see, and it worked but needed some sorting out after, and the Macosx partition was expendable - I was just testing. 

Have not tried it on an Apple partiton map scheme hard drive as used for Apple ppc.

By far the best approach would be to simply re-install Macosx from scratch in a smaller partition, after re-partitioning the whole drive using the macosx install dvd, leaving space for the ubuntu installer to do its thing dividing up the space later.

---

### Post by stmiller on 2007-09-18
The Ubuntu Edgy and Feisty live CDs do indeed have gparted on the CD. Make sure you disable journaling on your OS X partition, and back everything up. Gparted should be able to resize HFS+ once journaling is disabled, but I'm not 100% sure. Anyone?

---

### Post by Auria on 2007-09-18
> **stmiller said:**
> Gparted should be able to resize HFS+ once journaling is disabled, but I'm not 100% sure. Anyone?

I just did it a few hours ago :) yes it works, but of course backup everything first

---

