---
title: "Harddisk question"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-08-15
Hi, I was just wondering on one thing, when I look at my Ubuntu partition it says this:

Free Space: 2.3Gb
Available: 1.9Gb

Where has the 400mb or so gone? Is that my swap file? or can I recover it?

Calv

---

### Post by Denis on 2006-08-16
When you create an ext2/ext3 partition 5% of the disk space is reserved for the root user by default. This makes it easier for the root to work with the disk when it is filled by the user. 

You can see the amount of disk space reserved for root by running: 
```
sudo tune2fs -l /dev/[your partition]
```
The "Reserved block count" is the number of blocks reserved for root. "Block size" is the size of one block (in bytes). When you caluculate the size of the reserved blocks it should equal that space you lose. 

You can also change the percentage of reserved blocks with "tune2fs -m". It can be found in the manual of tune2fs. 

I've found this information [here]("http://www.tldp.org/LDP/sag/html/filesystems.html") and [here]("http://www.linuxquestions.org/questions/showthread.php?p=2360761")

---

