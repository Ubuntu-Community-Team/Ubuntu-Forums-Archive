---
title: "share personal folder between windows and ubuntu"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by rhase5 on 2006-12-20
hi there,

I am totally new to ubuntu and would like to do my first installation. I would like to keep Windows on the hard drive as well, so I could use both operatings systems.

My question now would be, if I could create one personal folder that I could use with both, Windows and Ubuntu. Or in other words, if I use Ubuntu and save an open office document in my personal folder, I would like to be able to access this document as well when using windows. Is this possible at all and what would I need to do? Create a third partition?

Also, what happens to my current personal folder and all the files in it once I install Ubuntu on a seperate partition. Can I access these files at all or only when using Windows?

Thanks so much for your help,
Rhase

---

### Post by jbayone on 2006-12-20
Yeah, you can access the Windows files in Ubuntu, you just have to mount the partition.

---

### Post by randiroo76073 on 2006-12-20
Here's some links that'll help:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

General topics:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

HTH

---

### Post by hal10000 on 2006-12-20
Best for sharing files between windows and linux is to create a fat32 partition, which you can easily read and write from within windows and linux.
If you want write permissions to a ntfs partition (win2000, winxp etc.) you have to install the ntfs-3g package. Read permissions to ntfs partitions are native.

---

### Post by jive_turkey on 2006-12-20
Definately create a fat32 partition like Hal10000 was talking about. There are apps that you can get for windows to read/write ext3 and for linux to read/write ntfs, but it is so much easier to create another partition for the two OS's to share. One simple step during install will save you some time later on.

---

