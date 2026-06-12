---
title: "Cant play Supreme Commander!!"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Link360 on 2007-02-25
Ive installed Ubuntu 6.06 on my computer with Windows XP. The partion gave Ubuntu a lot

more storage than Windows XP. Now im not able to install any new games for my 

computer,like Supreme Commander, because of lack of hard drive space in Windows XP. Will 

someone tell me how to give Windows XP more hard drive space without having to reinstall 

Ubuntu. Thanks in advance. Maybe this will give more information....

Disk /dev/hda: 100.0 GB, 

100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         568        2829    18169515    7  HPFS/NTFS
/dev/hda2               1         567     4554396    b  W95 FAT32
/dev/hda3            2830       11784    71931037+  83  Linux
/dev/hda4           11785       12161     3028252+   5  Extended
/dev/hda5           11785       12161     3028221   82  Linux swap / Solaris

---

### Post by oilchangeguy on 2007-02-25
from what i've read, you can use gparted to change the size of your partitions. and depending on the age of your windows install, a complete reload may not be a bad idea. or if you want remove ubuntu. while in windows, go to start, control panel, (enable classic view) admin tools, computer management, disk management. from there you can delete the ubuntu partition, and format it ntfs, and assign it another drive letter (i don't think you can make windows use the entire partition again as c:) and install your games in the new partition. and if you want to install ubuntu again, pay close attention to the partition segment of the install. you can allow some of the hard drive or all to ubuntu.

---

### Post by Link360 on 2007-02-25
how do you make an extended partion?

---

### Post by Link360 on 2007-02-25
Alright this is what my partions look like....

[http://www.ubuntuforums.org/attachment.php?attachmentid=13874&d=1154818078](http://www.ubuntuforums.org/attachment.php?attachmentid=13874&d=1154818078)

I want to get the unallocated into my  ntfs which is my windows xp i think. Does anyone know how to do that or know a better way. Thanks

---

### Post by oilchangeguy on 2007-02-25
right click on the partition. some things will be grayed out. please advise what is on the list, and what is grayed out. this assumes you're in windows control panel, not gparted.

---

### Post by Link360 on 2007-02-25
when i right click on the unallocated one all that i can click on is New the rest is grayed out. If i click on new it says that i can only have 4 primary partions and that i should make an extended one.

---

### Post by Link360 on 2007-02-25
bump

---

