---
title: "Do I need to partition my hard drive?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Notaguru on 2007-04-26
I downloaded Ubuntu 7.04, built a boot CD, and ran the OS off the disk to look it over. Seems fine!

To actually install it as an optional OS, must I first partition my hard drive?

My ultimate goal is multiple OS, with each having access to many of the same data files (word processing, spreadsheet, email (Thunderbird), browser bookmarks (Firefox), etc. 

Do I need a third partition for the data files?

---

### Post by zubrug on 2007-04-26
It's a good idea to keep a seperate home partition.

---

### Post by supersonicdarky on 2007-04-26
you will have to have atleat two partitions. 1 for ubuntu, 1 for windows. and if your windows partition isnt fat(32) you wont be able to write on to it, so you might want to make another partition with fat so you could transfer files back and forth

so right now, you need to resize your main partition and add one for ubuntu

---

### Post by Notaguru on 2007-04-26
Uh-oh. 
I need help figuring out how to do the partitioning. My data files are well backed up, but I have a lot of apps that would be difficult to replace (GiveawayOfTheDay stuff, for instance).

Can I change the partitioning without reformating the drive?

---

### Post by kolinab on 2007-04-26
I could try to explain it but would do a terrible job. There's some great explanation of what you are talking about here (it's called dual booting):

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Good luck, post back with more questions once you've read the basics there!

K

---

### Post by bobplano on 2007-04-26
> **supersonicdarky said:**
> and if your windows partition isnt fat(32) you wont be able to write on to it

there is something called ntfs3g and that allows you to read/write ntfs. about partitioning there is an automatic option during the install to resize your windows parition to make room for ubuntu. just make sure your windows partition is defragged or you might lose some things.

---

### Post by Midgetmunky13 on 2007-04-26
yes just do the install and it will ask you how you want to partition the hardrive.

---

### Post by supersonicdarky on 2007-04-26
> **bobplano said:**
> there is something called ntfs3g and that allows you to read/write ntfs.
;o

never heard of it. is it stable?

---

### Post by bobplano on 2007-04-26
yep it's stable. here's the site [http://www.ntfs-3g.org/]("http://www.ntfs-3g.org/")
and a howto: [http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by Sef on 2007-04-26
> there is something called ntfs3g and that allows you to read/write ntfs.


With Feisty, the easy way to install it is this:

Applications > Add/Remove > search > type NTFS > click on NTFS Configuration Tool > apply > apply > follow directions to finish.

---

