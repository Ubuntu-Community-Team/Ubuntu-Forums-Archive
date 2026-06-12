---
title: "Installing Edgy on the same drive as Dapper"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by MakLeod on 2006-11-10
I'm going to install Edgy to see how it works out in comparison to my current Dapper installation.  I've messed around with the partition editor a little bit, but I am still scared something might go wrong.  I tried going to the manual partition editor on the Edgy install, but it wouldn't let me set a "/" root partition because my root partition is already on the Dapper one.  I am going to backup my files just in case, but is there a Howto on installing Edgy while you still have Dapper on the same drive?  Last time I installed Dapper it decided to wipe my drive for me =(

---

### Post by ReaderRat on 2006-11-10
I am just a newbie, but here are some thoughts:
Download & Burn  [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)  Use it to remove any non-Dapper partitions you may have created. Install from the Edgy Live CD, and when you get to the "who am I" page, enter a different username & password than the ones you use for Dapper. Go on to partitioning, and select the "install to free space" option, and it should install from there on.

---

### Post by localuser on 2006-11-10
> **MakLeod said:**
> is there a Howto on installing Edgy while you still have Dapper on the same drive?

Here's a general howto for partitioning.  I found it by typing "ubuntu howto partition" in Google.  Google is your friend :)

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

