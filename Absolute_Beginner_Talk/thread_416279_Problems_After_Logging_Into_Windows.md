---
title: "Problems After Logging Into Windows"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by dunedust on 2007-04-21
I logged on to my windows partiton today after 3 months or so and these are the problems i experienced

1  All the files which i deleted from my windows partitions through Ubuntu were present in a folder called 
  " .Trash-Username" .This folder never showed up in Ubuntu.
     My partitions are formatted using FAT so I  did have the necessary permissions.

2  Kopete does not seem to deliver offline messages. Since it allowed me to send offline messages i assumed it     
   worked both ways .Is there a plugin i need to download to enable this feature?

---

### Post by jtraub on 2007-04-21
1. It is some kind of Windows Recycle Bin in Ubuntu. 
If you look at lower right corner of desktop you can see trash icon. Right click on it to empty .Trash folders

---

### Post by dunedust on 2007-04-21
Tthat seems to have worked

My trash is almost always empty
Only when i open the folder in which Ive loaded the partition trash gets loaded

anyway i think that solves my first problem

Thanks a lot

---

### Post by kahrytan on 2007-04-21
That is a HIDDEN folder in Ubuntu. You can make it show up under View menu in Nautilus.

---

### Post by dunedust on 2007-04-21
Yea i found the .trash folder after i used  ctrl+h
thankyou

---

### Post by jtraub on 2007-04-21
Any file or directory with . as first symbol is hidden in linux :-)

---

### Post by GSF1200S on 2007-04-21
> **dunedust said:**
> Yea i found the .trash folder after i used  ctrl+h
thankyou

Hmm.. i noticed the same thing the last time I logged onto windows. Right clicking on the trash can does not show any of the files. I looked in my NTFS partition for a folder called .trash with hidden files showing, and I didnt see it. Where exactly did you find it?

**never mind... I did an actual search and Nautilus found it.. thanks for the post though.. you guys just helped me!

---

### Post by jtraub on 2007-04-21
You should look for .Trash-<your username> on root directory of your NTFS partition. But I guess you haven't write support on NTFS partitions.
You can find trash folders on ext3/reiserfs/fat partiotions if you have deleted something on it.

---

