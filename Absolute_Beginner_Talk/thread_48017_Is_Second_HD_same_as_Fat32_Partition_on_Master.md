---
title: "Is Second HD same as Fat32 Partition on Master ??"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by KB8GT on 2005-07-10
I am awaiting my Ubunto Disks and have done some, I hope pre prep toward a great install.  They are 'in the mail'.

First from an old computer I installed a second hard drive -- 4GB.  At present it is Drive F:/ with FAT32 file system and empty.

Second I have read and read again many pages about installation of Linux.  From this reading, my major plan is to install a dual boot system.  My master hard drive is 80GB.  Plan is to resize Windows XP Home to around 50-60GB and leave the remaining 20-30GB for Linux.

I plan to use the install from Ubunto.  Do hope that I DO NOT make the mistake of selecting  'Erace entire drive'.  For sure I need to use the 'Manually edit partition table', and work my way though the procedure.   If all goes well I will have a dual boot system, or maybe I will be reinstalling both Windows and Linux

Question: Since I have the second hard drive as FAT32, need I make a partion and format it as FAT32 on the master drive - for file sharing - which is highly commended.  Or can my second hard drive serve that purpose.  I do not expect a great deal of file sharing between the two Operation Systems, but would like that option to be present from the get go.

Thank You
Larry

---

### Post by aysiu on 2005-07-10
Will you be filesharing only 4 GB of files? No music or large picture files? If so, then the second hard drive would be a great place to share files between as FAT32. Honestly, though, you won't need 20-30 GB for Ubuntu. Maybe more like 7 GB or 10 GB?

My suggestion would be the following:

1st Hard drive - 
15 GB NTFS for Windows XP
55 GB FAT32 for sharing between OSes
a small swap partition (double your RAM)
9 GB EXT3 for Ubuntu Linux

2nd Hard drive -
4 GB FAT32 to back up important documents every now and then.

By the way, if you just ordered your Ubuntu CDs, you'll have plenty of time to think about how to partition your hard drive. They can take around two months to arrive.

---

