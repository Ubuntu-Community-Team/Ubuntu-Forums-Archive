---
title: "Deleting Partitions (Where does space go?)"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by suberatu on 2008-01-03
I'm currently using Windows XP SP2, and am looking to dual-boot it with Ubuntu. I want to create partitions, but in order to do so I first have to free up some space. I have a 120 Gb hard drive which came pre-partitioned into C: (logical drive marked as boot), and D: (primary partition marked as system). I got hit with a really bad virus a while ago, and couldn't fix it myself, but wanted some files backed up. So, after sending it to a local repair shop, I now have C: and D: and files I asked to be backed up on G: (logical drive).

My question is, if I format and delete G: (I realize I will lose the data on it), where will the space go? Will it be automatically allocated back to one of the other drives (C: or D: )? Basically, how can I ensure that the space goes back to a drive from which I can partition?

---

### Post by Xavieran on 2008-01-03
First thing...download and burn the GParted Live CD ...

When you delete G: it will become un-allocated space.Then you simply select the partition closest to the un-allocated space and select Resize/Move then move the slider until it covers the unallocated space...

---

### Post by mikewhatever on 2008-01-03
That's right. Ubuntu installer can create partitions for Ubuntu in the unallocated space, the space you get after deleting a partition.

---

### Post by CouchMaster on 2008-01-03
To answer your questions -
If you reformat G with NTFS or FAT32 it will just be reformatted G space.
If you use ; say, GParted (a linux partition editor)- which I recommend, and format it with say ext3 - it will disappear from windows and become a Linux partition.
Ubuntu contains gparted so you could do it with the Ubuntu live CD.
You would need make G into 2 partitions though - one a small 1gig swap partition and the rest for Ubuntu.
I believe that if you just told Ubuntu to install itself to the G partition it would do everything for you automatically.
I would google 'dual booting' first and study this before I committed my HD to the process.

---

