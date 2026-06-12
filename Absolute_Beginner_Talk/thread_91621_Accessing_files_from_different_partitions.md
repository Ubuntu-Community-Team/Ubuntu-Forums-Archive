---
title: "Accessing files from different partitions"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by Chipface on 2005-11-17
I'm going to be setting up a dual boot system this weekend.  Win XP and Ubuntu obviously.  What I'm wondering is when I'm in Linux if I'll be able to access files from Windows and vice versa.

---

### Post by matthewv on 2005-11-17
[QUOTE=Chipface]I'm going to be setting up a dual boot system this weekend.  Win XP and Ubuntu obviously.  What I'm wondering is when I'm in Linux if I'll be able to access files from Windows and vice versa.[/QUOTE]
You'll be able to. Take a look at [http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html)

---

### Post by frodon on 2005-11-17
If you have NTFS partition, you will be able to read/write with windows and read only with linux but if yoiu have FAT32 partitions you will be able to read/write with both OS.
So if you want to be able to write datas on your partition with both OS i advice you to use FAT32 file system.

---

### Post by davmac on 2005-11-17
Vice - certainly. Versa, do-able but needs some new software installed on windows.

When you install Ubuntu you'll find that it automatically mounts your windows partition for you. I'm not sure of the latest state of play with NTFS formatted disks (the default for XP). Last time I looked, it was read-only access, but it could be that this has now improved. If you format the (or a) windows partition as vfat, you'll have no problems with read or write.

...and from the other direction, there are a number of things you can install to allow you to access your ext2 or ext3 partition. The one I'd tried was explore2fs from [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

Hope this helps,

Dave Mac

---

### Post by veebee on 2007-12-05
It looks like I have to re-install, but with many important files I want to install on seperate partition and wondering if I can acces those files from the new partition ?

Both will be kubuntu 7.04 64 bit.

Thanks

---

### Post by hyper_ch on 2007-12-05
generally speaking:

Linux can access ntfs and fat32 partitions
Windows can access ext2/3 and fat32 partitions

FAT32 is the simplest choice but it has two major drawbacks:
- files only up to 4 GB
- no journaling

the ext2/3 drivers must be additionally installed in windows
the ntfs read/write support must also be enabled in linux

If you have multiple linux systems, accessing linux filesystem partitions (ext2/3, jfs, reiserfs, ... ) is simple.

---

### Post by rahimveron on 2007-12-05
Install ntfs-3g to read/write access to your XP partitions and other NTFS partitions. Install it through Synaptic.

---

### Post by veebee on 2007-12-05
Thanks for the ultra prompt replies, but..

I know ( being relatively new to linux) this probably should have been in "absolute beginners" but when I'm installing the new version, how do I make sure its on a new. separate partition and the old stuff is still there and accesible? there are important files to do with my kennels etc.

Thanks again 
VB

---

### Post by hyper_ch on 2007-12-05
installing what new version?

---

### Post by veebee on 2007-12-05
sorry, when Im re-installing kubuntu Feisty

---

