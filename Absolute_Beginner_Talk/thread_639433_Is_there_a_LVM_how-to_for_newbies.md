---
title: "Is there a LVM how-to for newbies?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by mmcmonster on 2007-12-13
Is there a LVM how-to for newbies running Ubuntu?  I ask because a google search for LVM brings some pretty scarry pages without any simple examples that are relevant.

The best link I could find is [here]("http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem"), but it doesn't give any examples of how to resize the partitions later on.

---

### Post by dstew on 2007-12-13
If you really want to install Ubuntu on an LVM system, that link you have is as good as any. As stated, since there is no option to create an LVM system using the Ubuntu installer, you have to set up the logical volume using command-line tools from the lvm2 package, then install Ubuntu to the logical volume after that.

To resize partitions, you again have to use the LVM command line tools, like **lvresize**. See the [lvm2 man page]("http://linux.die.net/man/8/lvm").

---

### Post by skroops on 2007-12-13
You can set up LVM through the installer if you use the alternate disc.

---

### Post by mmcmonster on 2007-12-18
Thanks.  I'll give it a try next time I re-install.  Any links for examples?  The idea of LVM is appealing, but scary at the same time. :-)

---

### Post by Niniel on 2007-12-18
I've just done it myself, and believe me, you do not need any guides. Those things are just confusing people anyway. :)
Seriously, pop in the alternate install CD, select LVM - you can even encrypt your drive this way - and the rest is done for you by the installer. Piece of cake.

---

