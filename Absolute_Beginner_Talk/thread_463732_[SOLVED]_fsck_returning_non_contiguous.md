---
title: "[SOLVED] fsck returning non contiguous"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-04
I just did fsck on my external drive which wasn't being recognized on my Windows after my KoolDocl crashed and i had to hard reset.
 
This was the ouput:
```

[EMAIL="ubuntu@ubuntu:~$ fsck"]ubuntu@ubuntu:~$ fsck[/EMAIL] /dev/sdb1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
WD500 has been mounted 29 times wihout being checked, check forced.
Pass 1: Checking inodes, blocks and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 3A: Optimizing directories
Pass 4: Checking reference counts
Pass 5: Checking group summary information
 
WD500: ***** FILE SYSTEM WAS MODIFIED *****
WD500: 37085/61063168 files (1.8% non-contiguous), 17131312/122096000 blocks
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]

```
 
Is everything alright with my drive ?
What is the non-contiguous thing? Has my drive fragmented ? Its an EXT3 partition

---

### Post by freebird54 on 2007-06-04
That particular is a report on the 'fragmentation status' of the drive.  Contiguous can be defined as follwos:
```

1 : being in actual contact : touching along a boundary or at a point
2 of angles : ADJACENT 2
3 : next or near in time or sequence
4 : touching or connected throughout in an unbroken sequence <contiguous row houses
```

by the Merriam-Webster Online Dictionary - so you can see the relevance of the report!  BTW - not much is fragmented (1.8%) - so that isn't a problem

What I DON'T recognize is the 'Filesystem was Modified' message - not sure that that is about....

---

### Post by jonward0690 on 2007-06-04
> **Inxsible said:**
> I just did fsck on my external drive which wasn't being recognized on my Windows after my KoolDocl crashed and i had to hard reset.
 
This was the ouput:
```

[EMAIL="ubuntu@ubuntu:~$ fsck"]ubuntu@ubuntu:~$ fsck[/EMAIL] /dev/sdb1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
WD500 has been mounted 29 times wihout being checked, check forced.
Pass 1: Checking inodes, blocks and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 3A: Optimizing directories
Pass 4: Checking reference counts
Pass 5: Checking group summary information
 
WD500: ***** FILE SYSTEM WAS MODIFIED *****
WD500: 37085/61063168 files (1.8% non-contiguous), 17131312/122096000 blocks
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]

```
 
Is everything alright with my drive ?
What is the non-contiguous thing? Has my drive fragmented ? Its an EXT3 partition

Well your hard drive is ok your your system.Yes there is minor fragmentation but it is ok.

---

### Post by Inxsible on 2007-06-04
I just ran fsck on the same drive again and this is what i got
```

[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] fsck /dev/sdb1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
WD500: clean, 37085/61063168 files, 17131312/122096000 blocks
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]

```
 
I guess everything is alright now :confused:

---

### Post by Patrick K on 2007-06-04
1.8% is fine. I wish mine were that well off. My root partition is over 22% non-contiguous. And there isn't anything I can do about it.

---

### Post by freebird54 on 2007-06-04
Apparently your drive always was OK - the modified thing (now that I look more carefully) was only reporting that it successfully optimized the directories...

Does it work both places again now?

---

### Post by Inxsible on 2007-06-04
I havent logged into Windows yet.....will check now

---

### Post by freebird54 on 2007-06-04
K

Luck!

---

### Post by Inxsible on 2007-06-04
Its a crazy friggin' thing.

I just connected it to an old XP machine.....no love....... Windows just wouldnt see the drive. I even tried re-installing fs-driver.

Then i connected it to another XP machine and bam !!!

it recognized the drive and mounted it too in XP.

Only problem is that the old machine is on LAN and was used only to download torrents and store them on this 500 Gig mega monster drive. I guess I will have to think up another solution to that....

---

