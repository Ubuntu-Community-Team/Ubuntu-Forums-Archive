---
title: "Defraging Windows harddrive in Linux"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-25
Is there anyway for me to defrag my windows hard drive from ubuntu

---

### Post by Trymic on 2007-12-25
There is no need to defrag under Linux. I think it would only need if the hard drive is 95% full

---

### Post by Dapman01 on 2007-12-25
> **Trymic said:**
> There is no need to defrag under Linux. I think it would only need if the hard drive is 95% full

I understand that, What I want to do is defrag my WINDOWS partition while I am in Linux.

---

### Post by Rocket2DMn on 2007-12-25
NTFS still gets fragmented, but no, you cannot defrag from linux.  You will either need to boot into windows or mount the drive from another windows machine.  Sorry!

---

### Post by Dapman01 on 2007-12-25
Hmmm... i wonder why.  It seems kind of odd

---

### Post by jeffus_il on 2007-12-25
You could create a new partition the same size the one you want to defrag copy all files to the new partition and the copy all back after emptying the original one. Check out if this will cause any damage to your windows drive, (this works fine on linux file systems)

I have never tested this!

You could install a windows defragmenter under wine, maybe perfectdisk, or something similar.

Why do you want to do this?

---

### Post by Rocket2DMn on 2007-12-25
It is unlikely that windows defraggers would work under wine, and I wouldn't trust my data to that!  You should just reboot to windows and defrag from there.  I have not heard of anybody successfully defragging from within linux.
It isn't odd that you can't - there is no reason to have a defragger in a system that doesn't need to be defragmented!  It took them like 10 years just to get a program that was stable reading/writing ntfs which we now know as ntfs-3g.  I wouldn't trust them to get a defragger!

---

### Post by buccaneere on 2007-12-25
> **Trymic said:**
> There is no need to defrag under Linux. I think it would only need if the hard drive is 95% full

Linux volumes do not need defragmentation???

How is this?

---

### Post by kd7swh on 2007-12-25
NTFS tools in linux are really a new thing. Defragmentatition may come down the road but there isn't a tool out there to do it yet. 

Linux partitions don't get fragmented because of the fundamental differences in the structure of the ext2 and ext3 file systems.

fsck and badblocks are good tools for those (linux) systems.

---

### Post by vishzilla on 2007-12-25
> **buccaneere said:**
> Linux volumes do not need defragmentation???

How is this?

most of the Linux volumes use Ext3...this will give a clear understanding [http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

---

### Post by buccaneere on 2007-12-25
> **vishzilla said:**
> most of the Linux volumes use Ext3...this will give a clear understanding [http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

Good link vish...

Is there any graphical tool that at least shows disk usage, like the graphical analyzer in windows defragger tool (not referring to disk % usage - I found that)?

---

### Post by JillSwift on 2007-12-26
> **buccaneere said:**
> Good link vish...

Is there any graphical tool that at least shows disk usage, like the graphical analyzer in windows defragger tool (not referring to disk % usage - I found that)?Oh heck yeah - a fun one at that =^_^=

Applications -- Accessories --> Disk Usage Analyzer
('baobab' on the command line.)

Works on most file systems.

---

