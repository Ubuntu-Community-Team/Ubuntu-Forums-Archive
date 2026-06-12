---
title: "[SOLVED] Need help with Black screen"
date: 2008-11-05
forum: Apple Hardware Users
---

### Post by k.ashi.f on 2008-11-05
Hello everyone,

Just bought my first Macbook Pro 4,1. I am new to ubuntu and tripple booting Macbrook pro. I have been reading different forums to get as much info about ubuntu and triple booting as possible.

I am having problems with triple boot too. I downloaded rEFit on my MacBookPro(Penryn). I made two different partitions on my Macintosh HD by using terminal. I made the first partition MS-DOS FAT32, & the 2nd partition JHFS+. I installed XP on the first partition. The installation was complete. It asked me to restart. rEFit gave me the options to start either Mac osX or XP. I started XP and it worked perfectly. I updated the windows, installed some softwares and it was working great. 

Then I started the installation for ubuntu on the second partitation. During the installation I deleted the partition I made, made it a new partition with ext3 and mount on / then on step 7 of the installation i made sure that the boot file is also instaled on the same partition. The installation was complete and it asked me to restart.

rEFit is giving me the option to start either one of three systems. But for some reason when i try to start either XP or ubuntu. They don't work I can only start Mac osX and its working fine. But whenever I try to start XP or ubuntu all is see is the black screen and blinking curser on the top left corner of the screen. Nothing else. Can you please help me with situation. Thanks in advance.

Regards

---

### Post by overdrank on 2008-11-05
Hi and welcome, moved to Apple Users :)

---

### Post by cyberdork33 on 2008-11-05
make sure that your partition tables are in sync:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by k.ashi.f on 2008-11-06
Thank you so much. It helped me. The problem is fixed. I sync the tables in rEFit. It gave me the option to start any of the three systems. But Linux startup gave me the gray screen so did the windows. I started the system a couple of times and now its working fine. Windows is working nicely. Ubuntu is booting too but its just not working right. Its not giving me the option to shutdown. Something just not feels right. The mouse doesn't open the things I want to open. Plus the usual problems other users are having like, no wirless, getting too hot etc etc

So I guess I need to study some more threads. I am sure the solution is right here somewhere on this forum :) I am not leaving this forum ever now.

My heartfelt thanks to all of the helping people on this forum.

---

### Post by k.ashi.f on 2008-11-06
Can anyone please provide me information about the common issues after installing Ubuntu like wireless not working, being too hot, etc

Thanks

---

### Post by cyberdork33 on 2008-11-06
> **k.ashi.f said:**
> Can anyone please provide me information about the common issues after installing Ubuntu like wireless not working, being too hot, etc

Thanks


Wireless works if you select the proprietary driver provided in System > Admin > Hardware Drivers

Check the following:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by k.ashi.f on 2008-11-11
Thanks

---

