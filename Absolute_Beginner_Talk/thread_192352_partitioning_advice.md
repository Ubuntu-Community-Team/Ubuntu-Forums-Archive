---
title: "partitioning advice"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by tikas on 2006-06-08
i know that a similar thread has recently been posted but....
i have a 40gb harddrive i would like to duel boot windows xp and ubuntu what partitioning would you suggest?
thanks in advance
tikas

---

### Post by darkali on 2006-06-08
It depends on how much free space you have on your windows partition.
I'd recommend 3,5 to 10 Gb.
The more the merrier.

---

### Post by tikas on 2006-06-08
thanks
alot

---

### Post by aysiu on 2006-06-08
Read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by glotz on 2006-06-08
Windows and Linux do really *duel* boot! :)

---

### Post by red_shrike on 2006-06-08
Windows first and than linux. 8 Gb minimum if you plan on using Ubuntu on daily basis (recommended=:D :KS

---

### Post by Greevous on 2006-06-08
I have an issue: 

           I booted from the ubuntu cd that I made, and started to install ubuntu. I went through the manual partition process, dividing my drive into 4 partitions: an 80GB NTFS, an 82GB FAT32, a 20GB Ext3, and a 2GB Linux swap. I wanted to install Windows XP on the 80GB NTFS, but when I booted from my Windows CD, I can't see all of the partitions and the one partition that I do see claims that it is 127GB. Why are the partitions different when looked at through Ubuntu and Windows?

---

### Post by glotz on 2006-06-08
No idea, probably some MS quirk. You'll need to install windows first since it will overwrite master boot record destroying grub if you've installed linux allready. Probably can be repaired but...

So, start your windoze installer and make a 80 gig NTFS partition and install onto it. Then install linux and partition rest of the disk as you wish.

---

### Post by Greevous on 2006-06-08
So am only creating one partition for the whole drive when I install Windows, or should I leave the rest of it (everything except the 80G) unpartitioned? Then when I install ubuntu I can create new partitions in the unpartitioned space, right?

---

### Post by aysiu on 2006-06-08
[QUOTE=Greevous]So am only creating one partition for the whole drive when I install Windows, or should I leave the rest of it (everything except the 80G) unpartitioned? Then when I install ubuntu I can create new partitions in the unpartitioned space, right?[/QUOTE]
Well, it's up to you whether you want to do all the partitioning beforehand or you want to do it during the installation process.

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by SentientFluid on 2006-06-08
[QUOTE=Greevous]So am only creating one partition for the whole drive when I install Windows, or should I leave the rest of it (everything except the 80G) unpartitioned? Then when I install ubuntu I can create new partitions in the unpartitioned space, right?[/QUOTE]

I'm new but what I did was installed Windows and created 2 partitions with the Windows partitioner: 1 formatted NTFS for Windows (size is up to you), and then 1 unformatted for Ubuntu.  

When I installed Ubuntu, I deleted the unformatted partition and created 3 new partitions: a 10GB partition for /, a 2GB partition for /swap and the remainder went to /home.

hth

---

### Post by glotz on 2006-06-08
Linux installer can easily deal with the unallocated space.

---

