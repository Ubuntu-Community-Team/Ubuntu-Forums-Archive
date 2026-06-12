---
title: "NTFS, Fat32 and Ext3"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Talisker on 2006-07-27
I initally planned on using EXTIFS to share files between Win and Dapper.

I do have second thoughts about that tho.

I split my 60Gb HD into a 40 Gb NTFS Winxp partition (XP installed) and left a 16 GB partition RAW for Dapper.

My general Idea would be to use (mainly) word files with both OS. (whatever I decide to boot).
So, If I would make a small Fat32 partition (like 1 or 2 Gb) would that allow me to store files in that partition and access it from either OS, work on them and save it back to this location?

I'd appreciate the help, thanks! :D

---

### Post by Paerez on 2006-07-27
Yup, a fat partition is a nice swapspace between windows and linux. Mainly for linux->windows, since linux can read ntfs.

---

### Post by Talisker on 2006-07-27
ok.... so far so good. I assume that is common practice?

I noticed a few people in the forum dislike Fat32 in general. Is there something I should know about Fat32? *G*

Otherwise, I guess I'll go for that Partition Setup.

Thanks.

---

### Post by Third Thoughts on 2006-07-27
You may also want to check out the ntfs-3g driver
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)
It's still beta technically, but from what I've heard its quite stable. It allows you to read and write to ntfs, elminating the need for a fat32 partition.

---

### Post by professor_chaos on 2006-07-27
Yes fat32 is supported for read write for both of those operating systems and that scheme should work out good. If you like taking chances you can try looking at this project. [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/) I can't speak to whether its stable as I don't have an NTFS partition.

---

### Post by Talisker on 2006-07-27
Wow, sounds pretty good I like the NTFS-3g idea. *S*
Since I'm gonna do an install on a Ext HD first, I go for the Fat32 partition and then play around with the other program.

One more question, If I install Dapper on the external drive, does it install a dual boot manager on my primary C: drive? Or does it just make the external drive bootable? So it depends on my Bios what boots first?

Thanks, great help!

---

### Post by OU812 on 2006-07-27
And if you have your ubuntu paritions in ext3 you can get some tools to allow windows access to your linux partitions.

john

---

### Post by aysiu on 2006-07-27
> **OU812 said:**
> And if you have your ubuntu paritions in ext3 you can get some tools to allow windows access to your linux partitions.

john
[http://www.fs-driver.org](http://www.fs-driver.org)

---

