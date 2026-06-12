---
title: "HDD and parition problem!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by hobs0n on 2007-06-13
Ive been trying to get Xubuntu installed for the first time on my new server. I bought a new cheap HDD to I can have the OS on a seperate HDD from the other 4 HDDs, I managed to get get into the Xubuntu install after help from this [thread](http://ubuntuforums.org/showthread.php?t=421588). The problem I have now is in the install, in the partition part, it says that it failed to create a partition ext3 on the HDD under "guided - the whole disc". When I choose "manual" and create a SWAP and regular ext3 partitions it says it doesnt have any root system and that I have to fix that by the partition manager, have looked all over for that but havent found it anywhere.

Another weird problem is that the new HDD I bought to have the OS on, isnt visable in the BIOS anymore and I cant choose to boot from but both the Xubuntu install on the server and XP on my other comp sees it and I can make a NTFS format on it and copy stuff to and I have checked it with and found no faults or errors. Anyone know what this weird problem is about, faulty HDD?

---

### Post by ym4546 on 2007-06-13
> **hobs0n said:**
> Ive been trying to get Xubuntu installed for the first time on my new server. I bought a new cheap HDD to I can have the OS on a seperate HDD from the other 4 HDDs, I managed to get get into the Xubuntu install after help from this [thread](http://ubuntuforums.org/showthread.php?t=421588). The problem I have now is in the install, in the partition part, it says that it failed to create a partition ext3 on the HDD under "guided - the whole disc". When I choose "manual" and create a SWAP and regular ext3 partitions it says it doesnt have any root system and that I have to fix that by the partition manager, have looked all over for that but havent found it anywhere.

Another weird problem is that the new HDD I bought to have the OS on, isnt visable in the BIOS anymore and I cant choose to boot from but both the Xubuntu install on the server and XP on my other comp sees it and I can make a NTFS format on it and copy stuff to and I have checked it with and found no faults or errors. Anyone know what this weird problem is about, faulty HDD?
If you're having trouble with the installer's partitioner, try gparted alone, as in download the ISO and use that. I found (well this was when installing dapper) that using that seemed a little more reliable. That way, you won't have to do any hard drive stuff in the installer.

---

### Post by hobs0n on 2007-06-13
Ok will try that then :)

---

