---
title: "installing windows xp after ubuntu"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by qrm on 2006-04-23
Hi all!

Ive installed ubuntu on my laptop and im loving every second :)  All i need to do now is to install windows xp, but im not quite sure, how. I have a 100Gb hdd and ive allocated 45Gb to linux and 5Gb to fat32. So, i have 50 gigs of space for windows. Should i just put the Windows Xp cd in and it will recognize the free space itself?

thanks in advance;)

---

### Post by gr0kzer0 on 2006-04-23
I've never done a dual boot, but what I've read leads me to believe you need to install Windows first, or it'll overwrite your Linux partition.

---

### Post by qrm on 2006-04-23
well, as i understand, windows shoulnt even be able to see my ext3 filesystem, it should see only the free space or fat32 partition?

---

### Post by garner_nc on 2006-04-23
Your master boot record on your hard drive will be over-written by Windows XP because , hey, M$ knows nobody would be running any other operating system, right?

You can boot Ubuntu then install grub to a floppy drive. After you install XP and M$ fixes your hard drive for you, you can boot off the floppy and re-install grub to your hard drive boot sector. It will detect your XP install and set it as a boot option. 

All the Best,
Doug White

---

### Post by uzi09 on 2006-04-23
hey,

i recently just dual booted my comp with windows xp and ubuntu (dapper drake).

here is a thread i started before i did it because i was curious what type of partition setup would be best for me.

[http://ubuntuforums.org/showthread.php?t=151722](http://ubuntuforums.org/showthread.php?t=151722)

Princey also gave me the best site i've ever come across that teaches you how to dual boot and with LOTS and LOTS of PICTUES!!!

the site also has lots of different ways that u could dual boot (ex: just straight up one partition for xp, the other for ubuntu, or something more unique like havine one for xp the other for ubuntu and one more for ur home directory so that you can get xp (with a driver) to also use those files so that u don't have half ur things on one os and the other half on another!)

heres the link for it:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

enjoy - and good luck

uzi


ps: i too have heard that it's best to install windows first -- i did it that way myself too

---

### Post by Sef on 2006-04-23
> well, as i understand, windows shoulnt even be able to see my ext3 filesystem, it should see only the free space or fat32 partition?

Windows and Linux can both read and write to FAT32, ext2, and ext3.   The only difference between ext2 and ext3 is that the former has journaling included.

> The ext3 filesystem is a journaling extension to the standard ext2 filesystem on Linux. Journaling results in massively reduced time spent recovering a filesystem after a crash, and is therefore in high demand in environments where high availability is important, not only to improve recovery times on single machines but also to allow a crashed machine's filesystem to be recovered on another machine when we have a cluster of nodes with a shared disk.

[http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html]("http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html")

---

