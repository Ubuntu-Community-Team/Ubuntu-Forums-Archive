---
title: "[SOLVED] Graphical disk repartiton tool"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by tombacker on 2007-12-18
I have just got myself a new laptop (Dell Latitude D430) where I now have Windows and Ubuntu (version 7.10) installed.  The problem is that Ubuntu is now on a very large part of the disk, and I would like to make part of that one into a partition accessible to both operating systems.  I seem to remember from an earlier installation of Ubuntu that a GUI interface partitioner was available from the Administration menu, but now I am unable to find it. I would appreciate getting a pointer.  The solution may be to reinstall Ubuntu.

Tom

---

### Post by Efros on 2007-12-18
gparted should do it

sudo apt-get install gparted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) gives instructions for usage although it really is pretty straightforward.

---

### Post by PmDematagoda on 2007-12-18
Install Gparted using:-

```
sudo apt-get install gparted
```

That will install a partitioner which is usually recommended.

---

### Post by philinux on 2007-12-18
What windows is it. If vista dont use gparted - vista will bork.

---

### Post by tombacker on 2007-12-18
XP.  Should not be a problem.  And thanks all of you.

Tom

---

### Post by tombacker on 2007-12-18
Problem solved.  But it was a bit more tricky than just installing and using Gparted.  As far as I could see, you cannot use gparted on the partition you are using at the moment, and since the Linux partition was the one I wanted to reduce in size ... I did a new installation instead.  No real troble

Tom

---

### Post by Efros on 2007-12-19
K you should have tried the gparted live cd,

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

