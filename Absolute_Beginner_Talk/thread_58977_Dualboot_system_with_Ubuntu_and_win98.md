---
title: "Dualboot system with Ubuntu and win98"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by chris_wong on 2005-08-22
Hi.
I tried Ubuntu from the LiveCD and liked it very much. So I want to get rid of my current XP-installation and make a Ubuntu/win98 dualboot system (Win98 for old games and applications).

So I need to know... How would be the easiest way to do this? What do I install first? And can Ubuntu read and write to the Win98 partition?

Thanks in advance.

---

### Post by heimo on 2005-08-22
If you're installing "from scratch", install Windows first, leave some space for Ubuntu. Win98-partition will be read/write accessible from Ubuntu - I suggest one partition for this purpose.

See second section on this page:
[https://wiki.ubuntu.com/WindowsDualBootHowTo]("https://wiki.ubuntu.com/WindowsDualBootHowTo")

---

### Post by xmastree on 2005-08-22
Another option would be:
Partition your disk with a small primary partition, large seconday, and some umpartitioned space.
Install Windows on the primary, use the secondary for data and install ubuntu in the remaining space. That way if you trash the windows installation later, you can reinstall without touching the data.

Values of large and small depend really on what you're planning to do with the system. Whether or not you need room for games.

---

### Post by heimo on 2005-08-22
I reread my post and ... I wasn't too clear. :) I second xmastree - my "one partition" refered to data partition - one partition for just data and sharing between Windows and Ubuntu. That's actually how I like my Ubuntu, too - /home partition on its own, makes a lot easier to reinstall if neccessary (I run Breezy).

---

### Post by blacklantern on 2005-08-23
[QUOTE=heimo]If you're installing "from scratch", install Windows first, leave some space for Ubuntu. Win98-partition will be read/write accessible from Ubuntu - I suggest one partition for this purpose.

See second section on this page:
[https://wiki.ubuntu.com/WindowsDualBootHowTo]("https://wiki.ubuntu.com/WindowsDualBootHowTo")[/QUOTE]


Question--I heard from a friend that FAT32 was better to use as the file system because linux and windows can access those same files. Should I be doing NTFS of FAT32?

---

### Post by tedwoo on 2005-09-03
[QUOTE=blacklantern]Question--I heard from a friend that FAT32 was better to use as the file system because linux and windows can access those same files. Should I be doing NTFS of FAT32?[/QUOTE]

I would like to know that one too.  :?

---

### Post by Vulpus on 2005-09-03
[QUOTE=blacklantern]Question--I heard from a friend that FAT32 was better to use as the file system because linux and windows can access those same files. Should I be doing NTFS of FAT32?[/QUOTE]

Both Windows and Linux can ACCESS an NTFS file system but Linux CANNOT (in practical terms) _write_ to it!  If you want to read AND write from Linux and Windows you should stick to FAT32.

I have Ubuntu sharing a drive with XP but have set up a separate data partion formatted as FAT32 that XP and LInux can read and write to.  At first it was NTFS as I thought I wouldnt want to write to it from Linux, I was wrong!  So I had to convert it back to FAT32 with Partition Magic.

---

### Post by intel17 on 2005-09-03
How much Space would 98/XP Need for the Primery and how much would you say for the data and how much to leave?

Would it go something like 

30/60/10
30/30/40
40/30/30
30/40/30  ( In % )
Ect

Would would you guys say?
Thanks, Intel

---

### Post by Mustard on 2005-09-03
[QUOTE=intel17]How much Space would 98/XP Need for the Primery and how much would you say for the data and how much to leave?

Would it go something like 

30/60/10
30/30/40
40/30/30
30/40/30  ( In % )
Ect

Would would you guys say?
Thanks, Intel[/QUOTE]
 How big is your drive?

Windows 98 likes about 600mb of free space on its partion plus operating system.  I don't think there would be much file swapping going on between XP and Ubuntu, so I couldn't see the need for a very large FAT32 partition, depends on what the computer is being used for.  The data partition for XP/Win98 would have to be quite large because of the size of Windows games.

---

### Post by Vulpus on 2005-09-04
[QUOTE=intel17]How much Space would 98/XP Need for the Primery and how much would you say for the data and how much to leave?

Would it go something like 

30/60/10
30/30/40
40/30/30
30/40/30  ( In % )
Ect

Would would you guys say?
Thanks, Intel[/QUOTE]

An important thing to remember is that Windows needs at least 15% of free drive space  to be able to defrag efficiently.  I am a huge fan of Partition Magic and strongly recomend you aquire a copy.  On a dual boot system it is a huge advantage.  If you find that one partition is getting full (as happened to me two days ago) you can easily re-size it.  It also allows you change an NTFS partion to a FAT32,  _but_ read the following:

If you have PM Version 8 you need to upgrade to V8.01 AND THEN you have to install a patch from the PM website.  Without the upgrade AND the patch you get an error message (#1513) when trying to convert NTFS to FAT32 (and some other operations).  You have to search long and hard to find this info on the PM website though, I know this from experience.

See this link:

[http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/03ff4f1e5474fa6088256e75007cbc2f?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no](http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/03ff4f1e5474fa6088256e75007cbc2f?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no)

---

### Post by intel17 on 2005-09-04
[QUOTE=Vulpus]An important thing to remember is that Windows needs at least 15% of free drive space  to be able to defrag efficiently.  I am a huge fan of Partition Magic and strongly recomend you aquire a copy.  On a dual boot system it is a huge advantage.  If you find that one partition is getting full (as happened to me two days ago) you can easily re-size it.  It also allows you change an NTFS partion to a FAT32,  _but_ read the following:

If you have PM Version 8 you need to upgrade to V8.01 AND THEN you have to install a patch from the PM website.  Without the upgrade AND the patch you get an error message (#1513) when trying to convert NTFS to FAT32 (and some other operations).  You have to search long and hard to find this info on the PM website though, I know this from experience.

See this link:

[http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/03ff4f1e5474fa6088256e75007cbc2f?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no](http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/03ff4f1e5474fa6088256e75007cbc2f?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no)[/QUOTE]
 I have PM.  But im not sure what Version I have got, I will look it up.
I am not planning to Partion my HDD right now, but I have bookmarked all the information :D

Thanks for your answers, they where very Helpfull :D
Intel

---

