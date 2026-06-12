---
title: "Make partition bigger"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by newbie59 on 2007-03-13
When I first loaded 6.10, I wanted to limit my partition size in case I didn't like what I got or needed to go back to all windoze. Now, until I can upgrade my whole system, I want to move my partition from 70/30 to 50/50. Is there documentation available online to help me with this??  :guitar:

Thanks!!

---

### Post by confused57 on 2007-03-13
The gparted live cd is an excellent partitioning tool:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

There's also some excellent screenshots on the site.

---

### Post by newbie59 on 2007-03-13
thanks confused
much appreciated:guitar:

newbie

---

### Post by newbie59 on 2007-03-13
installed gnome partition editor and followed the visual instructions
in "partition", resize/move isn't available, with the following error message:
"unable to read the contents of this file system. because of this some operations may be unavailable. did you install the correct plugins for this file system?"
I installed gnome thru synaptic
any suggestions??:confused:

---

### Post by louieb on 2007-03-13
In order to resize a partition it cannot be mounted.  What that means you can't resize your Ubuntu partition while Ubuntu is running.   The way around this is as confused57     says. > The gparted live cd is an excellent partitioning tool:

---

### Post by chuckyp on 2007-03-13
Just boot to the ubuntu live cd and you should be able to use gparted and change the partition sizes.  The drives shouldn't be mounted when booting off of the live cd.  If they are you can just  umount /media/hda<whatever>.   Also be sure to defrag the windows partition before trying to shrink it.

---

