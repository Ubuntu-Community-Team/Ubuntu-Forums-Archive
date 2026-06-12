---
title: "Formatting"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-12-01
I have only 1 partition with windows on it and it is NTFS file system but I have 60GB of free space on it...is there a way for me to use the free space and create a new partition without deleting the windows? If so how?

---

### Post by lemonsCC on 2006-12-01
1) get an ubuntu liveCD (the regular one)
2) boot from it
3) open gparted
4) scale the NTFS partition down
5) create a new partition ext?/fat32?  (do you want windows access to this space?)

gparted is semi-intuitive if you need more details give a holler

---

### Post by jasrog on 2006-12-01
What do you mean by scale it down? How exactly? And scaling it down won't effect windows even though I only have the 1 partition?

---

### Post by lemonsCC on 2006-12-01
If you look in the image right clicking on a partition gives you the option to resize.  Click this and a box will pop up.  You can from here set the size in Mb of the partition you would like to make smaller.  The free space should be put "to the right" (after) the partition you just resized.

Right click on the free space (should be gray in color) and format to either ext3 (if you want to use it for ubuntu only) or fat32 (if you want access to this space from both windows and ubuntu.)

And no resizing the windows partition will not negatively affect it.  it will just rescan the partition next time it boots.

[IMG]http://gparted.sourceforge.net/screens/gparted_7_big.jpg[/IMG]

EDIT:  free space is called "unallocated space"

---

### Post by lemonsCC on 2006-12-01
ALSO...
After you click resize/move, a window that looks like this will pop-up

[IMG]http://gparted.sourceforge.net/screens/gparted_5_big.jpg[/IMG]

---

