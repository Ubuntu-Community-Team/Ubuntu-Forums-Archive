---
title: "Partition advice"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Nevtus on 2007-12-13
Hello, does this set up for partitions look ok for dual boot XP/Ubuntu? The sda1,sda2, and sda3 partitions are for my windows xp installation and I do not want ubuntu to go anywhere near them.

Advice is greatly appreciated :)

---

### Post by Sef on 2007-12-13
1) Make sure that Windows is on the first partition because it likes to be there.   

2) How much ram do you have?  You probably don't need to make the swap so big.

---

### Post by mozetti on 2007-12-13
Yeah, I'd cut your swap in half to 1 GB. You can also probably schrink the root partion (/) down to 8-10GB and use the rest to make your /home partition larger.

Also, if you're planning on using any of the ntfs partitions as dual-use, meaning you'd be writing to it from both XP and Ubuntu, then convert it to FAT32. Linux does have write-support to NTFS now, but it won't ever be perfect because MS won't open up the specs for NTFS. I always use the "better to be safe, than sorry" approach for NTFS and Linux.

---

### Post by psusi on 2007-12-13
You seem to have your / and /home backwards because /home is only 1 gig.

In fact, you really don't have enough space to bother with a separate /home.  / needs to be at least 5 gigs, preferably 7-10.  Unless you want to allocate more space to linux, then just use a single / partition.

---

### Post by ctyc on 2007-12-13
The general rule of thumb for swap is to make it the same size as the amount or ram you have.

---

### Post by dptxp on 2007-12-13
/ should be 4 GB minimum, but make it 6 GB minimum. Rest /home. SWAP 2GB is not too high if you are going to edit too many images at a time, else 1 GB is good enough.

---

### Post by Jeenyus on 2007-12-13
> **mozetti said:**
> 
Also, if you're planning on using any of the ntfs partitions as dual-use, meaning you'd be writing to it from both XP and Ubuntu, then convert it to FAT32. Linux does have write-support to NTFS now, but it won't ever be perfect because MS won't open up the specs for NTFS. I always use the "better to be safe, than sorry" approach for NTFS and Linux.
I was under the impression that ubuntu 7.10 has read/write capability to NTFS and there is an application to install for 7.04 that allows read/write the NTFS as well.  I could be mistaken so you might want to further research this.

---

### Post by mozetti on 2007-12-13
> **Jeenyus said:**
> I was under the impression that ubuntu 7.10 has read/write capability to NTFS and there is an application to install for 7.04 that allows read/write the NTFS as well.  I could be mistaken so you might want to further research this.

That's why I said Linux has the capability. But, until MS opens the specs on NTFS (don't hold your breath) any method that is developed has the inherent risk that something could go wonky. Now, ntfs-3g seems to be pretty well done. But, I've dealt with corrupted filesystems and lost data. Given the choice, I err on the side of safety.

---

