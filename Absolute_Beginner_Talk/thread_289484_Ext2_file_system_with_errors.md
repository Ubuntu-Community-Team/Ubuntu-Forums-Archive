---
title: "Ext2 file system with errors"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Whitebread1 on 2006-10-31
Hello, I formatted my music and picture storage partitions with the Ext2 file system so that both windows and Ubuntu would have full read and write access.  Whenever I boot into Ubuntu, I get messages saying that there are contiguity errors.  I formatted these partition with a gparted live cd and I'd like to remove these errors so I don't loose my data.  How can I fix these partitions?

---

### Post by Sef on 2006-10-31
Sounds like you need to defrag the partition.  Will check for the command to do it; don't know it off the top of my head.

Update: sudo fsck   

to learn more about it, in the terminal type this: man fsck

---

### Post by Iowan on 2006-10-31
If you have filespace available, it might be a good idea to backup the data first... I pretty well trashed a 6.06 system on bootup not long ago when **fsck** started finding problems.  By the time I let it "fix" things, the machine only halfway worked.
(I think that hard drive is failing - I don't reboot that machine any more...)

---

