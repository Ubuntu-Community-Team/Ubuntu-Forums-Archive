---
title: "Dual Booting 7.10 and Vista"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by stropyboy11 on 2007-10-25
Ok, I had 7.4, and I know how to dual boot with that. However, I wiped my computer because I was sending it back to HP and it voided my warranty to have Ubuntu. Anyway, as of now, I have an Ubuntu live disk and an empty 10 gig partition. Anyone wanna walk me through the rest? Pretty much the only thing I cant figure out is how to make a swap partition...

-Nick Stropko

---

### Post by stropyboy11 on 2007-10-25
I've got Vista Home Premium, a 7.10 live disk, and an empty 10 Gig partition....anyone wanna run me through the rest? The only problem I'm having pretty much is figuring out the swap partition....

-Nick Stropko

---

### Post by kellemes on 2007-10-25
Start here..
[https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo]("https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo")

Rule of fist.. Swap should be 2x memory with a max of 2Gb.

---

### Post by stropyboy11 on 2007-10-25
Anyone want to help me?

By the way, I'm running Vista Home Premium right now

---

### Post by snickers295 on 2007-10-25
in the livecd click the install icon on the desktop then follow that until it asks you what you want to do with the disk then select the manual partitioning. leave the partitions that were already on there alone and make a 8 gig partition and choose the  file system to be ext3 and the mount point to be /. then make a 2 gig partition and choose the mount point to be swap. then keep on going with the rest until you have Ubuntu installed

---

### Post by brn on 2007-10-25
Here is a good place to start: ```
 http://www.psychocats.net/ubuntu/installing#partitioning
```
The partitioner will remind you that you need a swap area.  Typically swap space should at least equal the size of your RAM and perhaps up to twice as much.  Wien I installed, the partition table showed that Vista actually occupied only about 3.8 GB.  The first partitioning option (automatic with dual boot) wanted to give Vista half the total disk so I used option #3 (manual) allocating a very generous 10 GB for Vista with the remainder for Ubuntu.

---

### Post by schneider707 on 2007-10-25
> **kellemes said:**
> Rule of fist.. Swap should be 2x memory with a max of 2Gb. O just wanted to say its 'Rule of thumb'...no offense, just wanted to correct ya

---

