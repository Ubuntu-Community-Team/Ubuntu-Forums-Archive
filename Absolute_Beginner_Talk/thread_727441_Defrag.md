---
title: "Defrag?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by OrneryGuy on 2008-03-17
Hi all, still new to Ubuntu, was wondering is there is a defrag program for Ubuntu? Have looked and haven't see one, thanks.

---

### Post by uberlube on 2008-03-17
EXT3 partitions don't need to be defraged. Lucky us! :)

---

### Post by Oldsoldier2003 on 2008-03-17
> **OrneryGuy said:**
> Hi all, still new to Ubuntu, was wondering is there is a defrag program for Ubuntu? Have looked and haven't see one, thanks.

nope. Linux filesystems can become fragmented over time but for the most part defragging is not required like it is on a windows system. The only time you really end up with substantial file fragmentation is if you are a heavy duty torrent down loader...

---

### Post by bodhi.zazen on 2008-03-17
There is a discussion of this very topic earlier today.

[http://ubuntuforums.org/showthread.php?t=712384](http://ubuntuforums.org/showthread.php?t=712384)

---

### Post by bruce89 on 2008-03-17
There is a bloody good explaination at [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by PeterJS on 2008-03-17
There is not a defrag program because most linux file systems don't need it. Ext3 defaults to using sparse file layouts so things don't fragment because they're all spread out. Also every 25-30 boots depending on disk size fsck will run to check the file system integrity, it automatically handles all the disk maintenance needed. Usually fsck doesn't find any errors the only incidence of errors I've heard of involved hardware crashes.

---

### Post by handydan918 on 2008-03-17
> **uberlube said:**
> EXT3 partitions don't need to be defraged. Lucky us! :)

Yeah, and neither do ext2, Reiser, HFS, 

Oh, wait. That's too long a list. Let's just list the ones that DO need defragging.
FAT32
NTFS

That's about it. It's just a coincidence that they are both built by M/S. 
No, really, it is. It certainly doesn't say anything about the competence (or lack thereof) of the Monkey-Men from Redmond...


:roll:

---

### Post by Tatty on 2008-03-17
Are there any non-M$ filesystems which need defragging?

---

### Post by bruce89 on 2008-03-17
> **Tatty said:**
> Are there any non-M$ filesystems which need defragging?

A good question spoilt only by the childish $ symbol.

---

### Post by Tatty on 2008-03-17
> **bruce89 said:**
> A good question spoilt only by the childish $ symbol.

Well having frequented the forums fairly regularly for over a year I have seen many people refer to microsoft as M$... from new users to much older veterans.

So i make sure I always do the same as i did not want to offend anyone.  There may be a very good reason for that designation which i do not know about - perhaps some copyright issue or perhaps simply some sort of courtesy.

I have never seen anyone else make any comment on this or give any reason for the existence of this spelling.  But it appears you  suddenly want to pick on me for this.  Thanks.

---

### Post by bruce89 on 2008-03-17
> **Tatty said:**
> But it appears you  suddenly want to pick on me for this.  Thanks.

I do this. I happen to think that using the $ sign is childish and pathetic. Criticism should be well constructed and well informed, not just a gesture of dislike.

---

### Post by 3rdalbum on 2008-03-17
> **handydan918 said:**
> Let's just list the ones that DO need defragging.
FAT32
NTFS

HFS
HFS+

---

