---
title: "Getting XP back with LILO"
date: 2005-06-30
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-06-30
I have finally managed to get Ubuntu up and running about 30%.

After numerous attempts to get Ubuntu working, I eventually did an "expert" install and in stead of GRUB I used LILO. (The only known change I made. The bad part is that LILO does not set up automatically for dual boot with XP. So I read the Linux How to's and found the solution, qouted here verbatim.

" When you open this file for the first time,
     you'll see that there is only one (or more) Linux entry. Well, you
     should know the exact position (read: a partition) where Windows NT
     has been installed, so you could add an appropriate entry into
     /etc/lilo.conf file. After you do that, restart Lilo and, after the
     next re-boot, you will have both 'linux' and 'nt' entries under
     Lilo menu."

The problem I that I do not have the slightest clue how to add the appropriate entry. The file have text that explains where and which portions should be changed for a dual boot, so in theory it is quite simple. BUT. There is HDE and HDA and HDD's etc. What is what? I know that XP sits on my first hard drive, formerly known as C-drive (Master) Linux is on the third drive, showing correctly in the config file as HDE3 if I recall correctly. If anyone can please check this out and suggest what the correct entry should look like, it would be much appreciated.

In case you wonder why I want to cling to XP. In UBUNTU I do not have:
Sound
Printer
Scanner
Dial UP
Bluetooth
Internet
CD writer
Email
And so I can list more and more, not to mention files on my other disks that is not available! Until I can bridge the gap, I will stick to XP. 

BTW. How can you access as root under the GIU? I cannot save, delete, change or do any file/disk operations other than opening files.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=GrootBrak]
BTW. How can you access as root under the GIU? I cannot save, delete, change or do any file/disk operations other than opening files.[/QUOTE]

this command: 

> gksudo nautilus

---

