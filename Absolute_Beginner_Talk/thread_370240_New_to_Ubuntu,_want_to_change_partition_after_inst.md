---
title: "New to Ubuntu, want to change partition after install"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by jamski on 2007-02-25
Just installed v6.10.  All is working well.  But now, I wished I had devoted more space to my XP partition.

How can I use QTParted to change the partition of my XP/Ubuntu installation? 
 
During the Ubuntu install on my 60 GB laptop, I gave to XP (NTFS), the other have for Ubuntu. But now, since XP is so much more of a "hog", I'd like to devote more to XP.  But when I try to use QTParted (run as root), the "resize" option is greyed-out on both the XP and Ubuntu partition. 
 
Suggestions? Can I use QTParted (or some other app) for this task, or would a re-install of both XP and Ubuntu be required?

---

### Post by jvc26 on 2007-02-25
When you're on Ubuntu you have the drive mounted as you are accessing it to use the files on it. Consequently you can't alter the partition while you're on Ubuntu - you need to use the [Gparted livecd]("http://gparted.sourceforge.net/livecd.php") for example, or the partitioner on the Ubuntu livecd to do it.
Il

---

### Post by Luk0r on 2007-02-25
Yes, use QTParted/GParted on the live CD if you want to resize the partitions.

---

### Post by kinematic on 2007-02-25
you can't resize partitions that are mounted so you will have to do this with a live cd such as [gparted](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.3-6.iso?modtime=1172154815&big_mirror=0)
just burn the .iso image the same way you burned ubuntu,boot from it and resize your partitions(backup any important data just to be sure).

edit:you guys beat me to it!

---

### Post by Luk0r on 2007-02-25
You could use the GParted livecd, but I don't see a point if you already have the Ubuntu one burned. :)

They both work.

---

### Post by zalym on 2008-06-06
Hello guys,

Can I use qtparted to remove the ntfs partition that i gave for xp and add it to my ubuntu partition?  

-- saleem

---

