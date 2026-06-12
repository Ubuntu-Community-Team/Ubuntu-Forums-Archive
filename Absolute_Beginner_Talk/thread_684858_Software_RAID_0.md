---
title: "Software RAID 0?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by feydrith on 2008-02-01
Hi...

I am in the process of putting together a system for file storage. I installed ubuntu onto a spare 20gb drive I had laying around. After the fact, I installed two 500gb drives. I would prefer to combine these drives into a **software **RAID 0 array. I have been looking through the forums for the past two days to find out how to do this, but havent had any luck finding anything I can understand. Unfortunately, I have very limited experience with linux in general. That's not to say I am clueless, but I would need someone to explain the process first. Can anyone give me an idea what I need to do? I grabbed LVM2, but that seems to be command line only... I would prefer a gui, but I can handle the command line with good instructions. 

Thanks in advance.

---

### Post by dcstar on 2008-02-02
> **feydrith said:**
> Hi...

I am in the process of putting together a system for file storage. I installed ubuntu onto a spare 20gb drive I had laying around. After the fact, I installed two 500gb drives. I would prefer to combine these drives into a **software **RAID 0 array. I have been looking through the forums for the past two days to find out how to do this, but havent had any luck finding anything I can understand. Unfortunately, I have very limited experience with linux in general. That's not to say I am clueless, but I would need someone to explain the process first. Can anyone give me an idea what I need to do? I grabbed LVM2, but that seems to be command line only... I would prefer a gui, but I can handle the command line with good instructions. 

Thanks in advance.

Are you aware that "RAID 0" actually has no "Redundancy" whatsoever and doubles the chances of losing all of your data? (if just one drive fails, you lose all data on both drives).

Having striped drives listed in the RAID categories is just about the biggest misleading thing in IT, "RAID 0" is the exact opposite of "Redundancy" - you totally sacrifice it for the convenience of a single logical drive and some minor performance gains.

---

### Post by Roger Mudd on 2008-02-02
Not sure about RAID 0 -- as I wasn't looking for mass storage. I'd agree with dcstar that RAID 0 probably isn't the best answer for a file server. I went RAID 1 with two 500 GB drives and install from scratch was relatively painless. This tutorial was extremely helpful and may very well work for RAID 0 should you decide to go that route:

[URL="http://users.piuha.net/martti/comp/ubuntu/en/raid.html"]
RAID1 in My Ubuntu Installation[/URL]

---

### Post by feydrith on 2008-02-05
I'm sorry, I probably should have indicated that I have a fairly extensive amount of experience with PC's and I do actually know what I'm doing in general. Like I said, the last time I touched Linux was almost 8 years ago now and I really only remember the basics. Besides, I'm sure things have changed since then. 

I know the differences between RAID 0 and 1. I'm aware of the benefits and draw backs. In this particular situation, I would prefer RAID 5, but that's not an option. I need a terabyte of storage space. The system is a backup of a backup, so it's very existence is redundant. At some point in the near future I plan to add another drive for RAID 5, but for now I just need to get this up and running.

---

### Post by feydrith on 2008-02-06
I've made some progress in building the array by following various guides, but I still cant seem to get it mounted right. On top of that, the drive is significantly smaller than it should be... the 500gb drives show up as 465gb in gparted and the array is listed at 931gb, but once I mount the array the drive space drops down to 870gb.

---

