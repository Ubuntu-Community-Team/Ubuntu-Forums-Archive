---
title: "hard drive issue"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-12-21
cannot access hard drive from any medium can't install grub or xp mbr image can't install ubuntu I get a error about a logical block. Cant install xp I get an error while updating partition info. Both can mount the drive but neither can read or write it. Parted Magic can mount it but shows no files. When I try to use gparted it gets hung on scanning disk. I also got a message about I/O error and a bios bug. the machine is  
a HP pavilion zv5000 pentium 4 3gh 368mb RAM. I can't delete the partitions either. Is this hard drive cooked?

---

### Post by thelatinist on 2007-12-21
Does your bios find the drive?

---

### Post by swoll1980 on 2007-12-21
yes

---

### Post by Sef on 2007-12-21
1) Partition Magic and Linux tend not to get along well.

2) Try [Knoppix]("http://knoppix.com") and see if you can access your hard drive with that Live CD.  If you can, then use a usb key to save your files too.

---

