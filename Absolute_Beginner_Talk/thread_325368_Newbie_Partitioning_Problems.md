---
title: "Newbie Partitioning Problems"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by alexliggett on 2006-12-25
I'm a definite newbie, so bear with me.  I just receieved a dell inspiron 1501 for xmas, and straight out of the box I'm wanting to install Ubuntu.  Everything goes just fine until I reach the part where I have to Partition disks..   the only method my computer offers me is to "manually edit partition table".  In the handy "beginning Ubuntu Linux" book i have, it shows 4 options and tells me to choose the first: "resize IDEI master.."  Not sure what to do. :-k

---

### Post by mulligan.can on 2006-12-25
Are you wanting to dual boot the machine?

---

### Post by taurus on 2006-12-25
If you only have one harddrive, it's better to resize it using gparted from the LiveCD, leaving room at the end of the harddrive to install Ubuntu.  Then, click the installing icon and tell the installer to use the empty space.

Maybe this will give you a hint.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by lucky_chouhan on 2006-12-26
I want to know more thing like.

1. you use any windows 
2. you want dual boot.
3. you have another hd for your data or your data on exist disk.


i am working with 3 OS.
C:\Windows Xp           10 GB
D:\Windows 2003        10 GB  
E:\Downloads              20 GB
F:\Torrents I               20 GB
G:\ Torrents II            20 GB 
H:\ Personal               10 GB
Ext3:\ Ubuntu             15 GB

---

### Post by redDEADresolve on 2007-01-02
> **alexliggett said:**
> I'm a definite newbie, so bear with me.  I just receieved a dell inspiron 1501 for xmas, and straight out of the box I'm wanting to install Ubuntu.  Everything goes just fine until I reach the part where I have to Partition disks..   the only method my computer offers me is to "manually edit partition table".  In the handy "beginning Ubuntu Linux" book i have, it shows 4 options and tells me to choose the first: "resize IDEI master.."  Not sure what to do. :-k

[http://ubuntuforums.org/showthread.php?p=1782230#post1782230](http://ubuntuforums.org/showthread.php?p=1782230#post1782230)

read this thread, go through the whole thing so you understand both options 

i recommend the pci=nomsi option

---

