---
title: "[SOLVED] Problems Installing Ubuntu 7.04"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Ballping on 2008-04-20
Tried doing a search but couldn't find any threads that answered my issue.

A little info first:

Have 2 hard drives. 

1st hard drive has win xp on it.

2nd hard drive is partitioned into 3 parts. 62 gigs is NTFS partition. 13 gigs is Ext3 (not sure if this is what i'm suppossed to be partitioning as, i had ext2 and ext3 as options so i chose ext3). 1gig of the hard drive i set as Swap.

The installation goes to almost complete and then i get an error message. " grub-install (hd0) failed, this is a fatal error. "

Then the installation program closes out. If anyone has any idea about what could be going on i'd greatly appreciate it.

The hard drive is a 80gig Sata.

Thanks.

---

### Post by Ballping on 2008-04-21
Well i played around with it a bit more and managed to fix this issue. I changed the EXT3 formatted partition to EXT2 format and grub installed successfully. 

As i'm a total noob to Linux this is just a wild guess but i'm guessing that the version of grub that was trying to be installed was not compatible with the format version i was trying to use.

If anyone could confirm or deny this for me that would be great as i'm still trying to learn Linux's file structures and rules.

Thanks.

---

### Post by laffinet on 2008-04-21
Did you change anything else ? 

By no means am  I an expert, but I don't think the ext3 file system would have been the issue. I've installed both 7.04 and the 8.04 beta on ext3 file systems without any problems.

I did a bit of a search in the forum and also googled your problems. There are quite a few people out there with a similar problem. Doesn't seem to be a file system issue, more a problem of conflicting drive allocations between BIOS and grub.

I therefore suspect you changed something else and that fixed it. Any idea what else you might have done ?

---

### Post by Ballping on 2008-04-21
No didn't change anything else. The only other thing that could be it is i read a thread where someone was having a similar, but slightly different issue with grub, and they unplugged their router to prevent linux from trying to access the internet while installing, so i unplugged my cell phone (i use my cell phone as a modem) from the PC. Do you think that could possibly be what fixed it?

> **laffinet said:**
> Did you change anything else ? 

By no means am  I an expert, but I don't think the ext3 file system would have been the issue. I've installed both 7.04 and the 8.04 beta on ext3 file systems without any problems.

I did a bit of a search in the forum and also googled your problems. There are quite a few people out there with a similar problem. Doesn't seem to be a file system issue, more a problem of conflicting drive allocations between BIOS and grub.

I therefore suspect you changed something else and that fixed it. Any idea what else you might have done ?

---

### Post by laffinet on 2008-04-21
Yeah, I saw that thread as well. No idea if that's got anything to do with it.

I guess the good news is that you managed to install Ubuntu, so enjoy :D 

And if you really want ext3, google "convert ext2 ext3", there are plenty of guides out there that tell you how to do it. I did it once, wasn't a problem at all.

---

