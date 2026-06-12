---
title: "Help W/ Partitions"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by CyberKiL on 2006-08-27
Hello, I'm going to install Ubuntu from the Live CD and I have already made my 232 gig partition 205 gigs to give me about 27 gigs for the main ubuntu partition. 

If I have 1 gig of ram I should make  a linux-swap partition that is 2 gigs?

And that would leave me with 25 gigs left for the main ubuntu partition. I think I should use ReiserFS because that was recommended over ext3. Can I upgrade to reiser4 from there? Can I read/write easily with my windows ntfs partition and my ext. HD?

Could somebody help me out as to how to do this as I am new to partitioning and ubuntu. I'm starting out with my 205 gig NTFS partition and the rest is unallocated. Step by Step would be great :)

---

### Post by bodhi.zazen on 2006-08-27
I would use swap of 2 Gb, if you do not run memory intense programs, however, you may be able to do with less.

Not sure if you will see much difference between reiserFS and ext3. I used to use ReiserFS, now I use ext3. Ext3 may be more compatible with Windows.

Last, yes you can rw your nfts partition and external HD. Set the mount point(s) at install.

Write to ntfs is considered experimental and I would no advise it if your Windows partition is "mission critical" to you. With that said, I have a nfts partition I use rw with Linux without problems (yet....).

---

### Post by CyberKiL on 2006-08-27
How should I set the mount points? That's where I'm most confused. And does it matter in which order I make the partitions? For example the unallocated 27 gigs can go towards the the ext3 which is logical right? and the 3rd partition would be the 2 gig swapfile?

---

### Post by Bachstelze on 2006-08-27
The mount point are whatever you want. It is the directory where the partition's files will be located.

---

