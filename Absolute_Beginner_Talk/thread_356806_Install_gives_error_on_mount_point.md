---
title: "Install gives error on mount point"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by i-love-linux on 2007-02-08
I have been trying to install Edgy 6.10, but when I get to the manual  partitioner, and choose hdb4, and the mount point of root "/", when I continue it gives me an error:

[COLOR="Red"]No root file system[/COLOR]

How can this be when I have choosen "/", what would cause this ? I have tried google searches and Ubuntu documentations and can not find an answer.

---

### Post by taurus on 2007-02-08
Did you remember to tell the installer to format /dev/hdb4 to ext3?

---

### Post by i-love-linux on 2007-02-08
> **taurus said:**
> Did you remember to tell the installer to format /dev/hdb4 to ext3?

Yes, I sure did !

---

### Post by confused57 on 2007-02-08
If I remember correctly, several people have had this problem with the live cd installer:
[http://www.ubuntuforums.org/showthread.php?t=310801&highlight=no+root+partition](http://www.ubuntuforums.org/showthread.php?t=310801&highlight=no+root+partition)

You might want to try the gparted live cd(approx 30 mb download) to set up your partitions beforehand:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It's a handy partitioning tool to have around anyway, kind of like Partition Magic, except it's free & works better with Linux than PM.

---

### Post by i-love-linux on 2007-02-08
> **confused57 said:**
> If I remember correctly, several people have had this problem with the live cd installer

Ok, I'll get out my Gparted Live CD and format it with that. One of the links you provided seemed like that is what is needed, must be a bug !

---

### Post by i-love-linux on 2007-02-08
I got it to install after formating it with Gparted Live CD. But it still would not continue without checking the format box which also seems strange. I hope the developers have addressed this bug !

Thank you all for the tips that led me to this work around......

---

