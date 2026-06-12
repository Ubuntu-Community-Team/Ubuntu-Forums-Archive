---
title: "NTFS Partition question"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by Signguyhuss on 2006-04-20
When i installed linux, in the partitioner i accidently it to 'use this partition' for my NTFS partition . The result is that when i go to the system monitor, the NTFS drive is there.
I then went to System>Admin>Disk, and told it to 'disable' the status of this ntfs partition. Now i cant see it at all.
My question is: is this totally safe? This ntfs partition contains my Windows install that i use to dual boot. Is there any chance , in the worst case scenario, Ubuntu could screw with the files on there?


Cheers

---

### Post by Borniet on 2006-04-20
If I'm not mistaken, your NTFS partition will standard mount 'read-only', this is because the 'write' part of the NTFS driver is not yet stable enough (last time I checked).
This means that your partition is safe.

---

### Post by Sef on 2006-04-20
Linux can read, but not write to NTFS partitions.  

If you want to have Windows and Linux share files, then you will need to have a FAT32 or ext2 partition.

---

### Post by Borniet on 2006-04-20
[QUOTE=Sef]Linux can read, but not write to NTFS partitions.  

If you want to have Windows and Linux share files, then you will need to have a FAT32 or ext2 partition.[/QUOTE]

Just for the correctness of the story:
Linux can read NTFS, and can write to NTFS too, IF, and only if, the filesize doesn't change.... This means that you cannot add 5 chapters to the manuscript of your first 900 page war-novell, but that you can change the typos in it from 'teh' to 'the'. Also, when you want to start writing your second manuscript, for a science-fiction novell a la 'Taken', you cannot create the new file from within Linux on your NTFS partition.
Small recap: writing to NTFS is in practice pretty unuseable.

---

### Post by ec2 on 2006-04-20
I've heard, that you can write NTFS partitions, but then Windows Might not recognize them. So to be on the safe-side, i would suggest not to mess with NTFS partitions in any Linux, if you have some extremely important information on them...

---

### Post by Signguyhuss on 2006-04-24
Cool. Thanks for the help guys
i ended up just re-installing Ubuntu but made sure all the ntfs drives were explicitly not to be used. Better to be safe than sorry ;D

---

