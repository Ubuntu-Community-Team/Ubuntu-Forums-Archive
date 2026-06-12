---
title: "installing with partitions"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by xerox on 2007-01-06
A few questions:

1) How much space is recommended for a partition for Ubuntu if you have 22GB of free space (from your windows install/partition) and still plan on using windows ocasionally?
2) Which filesystem to use? Are there any special programs to be downloaded for capability (ie to recognize Ext3 filesystem)
3) What a linux-swap partition is used for
4) Does resizing partitions damage the windows boot?:-k 
5) And finally, if it's possible to transfer some files from windows (ie. text, pictures) to linux, in order to gradually lessen dependence on windows?

Misc. info:
Using a laptop with wireless (can't get it to work; but that's not urgent as I have a previously used wired connection that does work)
No backup of windows program files

Thanks in advance - I'm halfway through the install (got the ISO image on a disk, and am booted on Ubuntu right now actually)

---

### Post by Bachstelze on 2007-01-06
1) 5 GB is usually more than enough for an Ubuntu installation. Use 7-10 if you want to have space to fiddle with stuff.
2) Matter of tastes, I personnaly use ReiserFS but if you want to access your Linux partitions in Windows, ext3 is the way to go.
3) Equivalent of Windows' "virtual memory", more info [here](http://en.wikipedia.org/wiki/Swap_space#Swapping_in_the_Linux_and_BSD_operating_systems).
4) Most often, it doesn't but the "zero risk" doesn't exist so backup valuable data first. Running a defrag of the partition in Windows befor resizing can help, too.
5) Yes :)

---

### Post by hyper_ch on 2007-01-06
1.) You need a least two partitions (SWAP and "/" [Root]), however 3 partitions are adviced (SWAP, "/"[Root] and "/home")

2.) SWAP is the same as the pageinfo.sys (or something like that on windows). I uses diskspace to create more RAM... but SWAP of course is slower than conventional ram... as a general rule you can make it double your ram size

3.) If you have a separate /home partition then the Root partition should at least be 5-7 GB in space... this is need for various things, however I have min set to 15 GB (just to be sure).. otherwise assign the space you want to it... the more the better...

4.) Everything else can go into "/home" if you... I would give at least 4-5 GB for it... but the more the better....

According to your point (1) I take you have windows installed and 22 GB of diskstapce free?
Well, then use double ram size as Swap and maybe 10-12 GB for the root (and home) partition... so you still have like 10 GB free... with that you can create a FAT32 partition so that you can exchange files easy between your windows and ubuntu install

Resizing shouldn't damage the windows boot however you should make backups before you resize. Although chances are very, very slim that something goes wrong **it can happen!!!** And for that case you do want to ahve backups.

---

### Post by xerox on 2007-01-06
Thanks for the quick replies :)

---

