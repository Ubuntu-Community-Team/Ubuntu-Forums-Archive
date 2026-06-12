---
title: "External hard drive mount problem..."
date: 2016-11-17
forum: Apple Hardware Users
---

### Post by Furycd001 on 2016-11-17
HI guys

A few days ago I had a problem mounting my external hard drive with read & write function **>> [https://ubuntuforums.org/showthread.php?t=2343030](https://ubuntuforums.org/showthread.php?t=2343030) <<** As the thread shows I managed to get everything sorted. That is until today... Today thunar file manager happened to lock up whenever I was copying a large folder from the drive to my internal drive. After leaving everything alone for a while thunar decided to force close itself. Upon clicking on the hard drive's icon on the desktop I received the following message **FAILED TO OPEN DIRECTORY ELEMENT. Error opening directory '/media/furycd001/Element': Permission denied.** After closing the error message I decided to reboot. Upon rebooting my laptop my external hard drive now mounts as **/media/furycd001/Element1/** instead of **/media/furycd001/Element **which is what it was mounting as originally. The hard drive name still shows as **Element** on the desktop icon and in thunar. Everything on the drive has now reverted to a read only state and the commands used in my previous post do not work. Could someone please help me to get my external hard drive mounting back as **/media/furycd001/Element/** with read and write privileges. I just need to copy a few more things from the drive before I can reformat it to work better with Linux. Many thanks in advanced for your help.

---

### Post by Furycd001 on 2016-11-19
Using an osx install disk I was able to copy the files I need to another dirve. Formatted the drive in question using gparted...

---

