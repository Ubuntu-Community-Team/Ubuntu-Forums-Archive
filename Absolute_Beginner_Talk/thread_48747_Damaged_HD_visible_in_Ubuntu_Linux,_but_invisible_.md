---
title: "Damaged HD visible in Ubuntu Linux, but invisible in WinXP"
date: 2005-07-13
forum: Absolute Beginner Talk
---

### Post by ign on 2005-07-13
hi to all,
excuse me if this is a bit off-topic, but i've seen this is a very friendly forum and have solved many of my linux-newbie doubts browsing here.
i have an external hd that i used with a winxp system. it is/was formatted in the ntfs system. after a bad disconnection, windows couldn't see it anymore, it just detected an unformatted disk.
afterwards, during a disk check, i got some phisical error messages.
now i'm making the transition to linux and have a dual boot, with the same winxp home and ubuntu on it. to my surprise, when i access the drive using the shell (not the case using the gui, it freezes) i can see all the files and folders in place, but can't reproduce them or copy or move them, i get 'error de entrada/salida' which means 'in/out error'. it's mainly mp3s.
do you think there is a way of recovering this data using Linux, or should i forget about that?

---

### Post by maruchan on 2005-07-13
Hi ign,

Maybe something like this helps?

[http://migs.paraz.com/w/archives/2004/10/06/losing-and-recovering-my-ntfs-partition/](http://migs.paraz.com/w/archives/2004/10/06/losing-and-recovering-my-ntfs-partition/)

[http://help.lockergnome.com/lofiversion/index.php/t27168.html](http://help.lockergnome.com/lofiversion/index.php/t27168.html)

---

### Post by ign on 2005-07-14
thanks for the advise, 
link #1 : looks promising, but i'd need a more step-to-step find of guide, the commands mentioned there have many options (like dd) and i don't want to put on risk possibilty of recover.
the same applies to the 2nd link, which is more related to repairing a damaged boot drive using a live cd. my drive is external and only has documents and music on it and my pc has already ubuntu installed.

UPDATE: a part of the file can be copied to a different location, you'll see the icon but the file,for example a 5 M mp3 is only 480 kib, 20 sec long  :?

---

### Post by AntiDragon on 2005-07-14
Seems to me you've got a damaged/incorrect MFT (Master File Table) on the disk.

The MFT supplies basic information about the disk and it's structure as well as the index used to locate data on the disk. If it's damaged the first problem is that Windows will not recognise the disk properly - it will assume a foreign file format or think the disk is unformatted.

The NTFS support in Linux works differently. When you mount the drive you're pre-specifying the filesystem so Linux already knows it's NTFS (as opposed to Windows which tries to find out on it's own). Subsequently, you can browse the disk as much as the MFT will allow.

Good news is that a damaged MFT doesn't nessecarily mean any of your data is lost.

Bad news is (and I hope someone can prove me wrong!) all recovery tools that can handle damaged MFTs cost money. So , bearing in mind that there are no guarantees on success, you have to decide if it's worth the chance.

Some I've found are:

[http://www.partition-recovery.com/](http://www.partition-recovery.com/)

[http://www.ptdd.com/index.htm](http://www.ptdd.com/index.htm)

[http://www.runtime.org/recoverability.htm](http://www.runtime.org/recoverability.htm)

---

