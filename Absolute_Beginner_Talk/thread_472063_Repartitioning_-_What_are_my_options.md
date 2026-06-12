---
title: "Repartitioning - What are my options?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by nylecoj813 on 2007-06-12
Hello everyone,

I decided to setup a dual boot Windows XP Pro/Ubuntu (Feisty Fawn) on my Dell Latitude D610 a few weeks ago. Everything is going great (I used Ubuntu 6.06 on an older desktop and loved it, but I am loving it even more on my faster laptop :-P) 

However, I made a slight misjudgment when installing, and I now wish that I had a larger XP partition, mainly for games. I have been using Ubuntu otherwise ^_^

What I would really like is for XP to have 40gb (giving me about 15 more gb to work with) and then leave the rest for Ubuntu. I am not completely against reinstalling Ubuntu to set this up correctly, I have backed up using this method ([http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)). However, if there is an option that doesn't require a reinstallation, I'm all for that.

Attached is a screen shot of my partitions in gparted. What options do I have here? 

If you need any more information, let me know! Thanks a lot!

---

### Post by Bohlio on 2007-06-12
I think your kinda outta luck, check out this thread... [Repartition Dual boot]("http://http://ubuntuforums.org/showthread.php?t=472057")

---

### Post by durrell on 2007-06-12
You're not out of luck. Resize the Linux partition, then resize the Windows partition. Gparted will move the Linux partition to the right and then "grow" the Windows partition to the desired size. Be prepared to wait, though..I did this last night except I made my Windows partition smaller and my Linux partition bigger. At least I think it should work the same, I don't know why it wouldn't since you're moving the Linux partition as a whole. It took me about 2 and a half hours of waiting for gparted to finish.

---

### Post by Bohlio on 2007-06-12
Oh, Im sorry. I was under the impression that Gparted couldnt do that :-) please ignore me. :-)

---

### Post by mikewhatever on 2007-06-12
Well, I've never resized a partition to the right, but you can try. The worst thing that can happen is reinstalling Ubuntu, no big deal. I'll try checking the documentation for gparted.

---

### Post by nylecoj813 on 2007-06-12
> **durrell said:**
> You're not out of luck. Resize the Linux partition, then resize the Windows partition. Gparted will move the Linux partition to the right and then "grow" the Windows partition to the desired size. Be prepared to wait, though..I did this last night except I made my Windows partition smaller and my Linux partition bigger. At least I think it should work the same, I don't know why it wouldn't since you're moving the Linux partition as a whole. It took me about 2 and a half hours of waiting for gparted to finish.

See, I actually tried doing this. I resized my Ubuntu partition, and when I tried to grow the XP partition I was not allowed to increase the size. What I mean is that, the maximum size it said I could expand it to was already the size of the partition :confused: All I had was unallocated space that I couldn't format as a primary partition because I can only have 4.

I am going to boot up my gparted live CD and have another look, maybe I missed something the first time through.

bohlio: thanks for the link though!

**Edit**: I apparently was not shrinking the linux partition correctly. I've resized exactly how I wanted and both XP and Ubuntu work fine :) Thanks for the help!

---

### Post by rlgoddard on 2007-07-02
Hi,
 
I don't mean to threadjack, but I have a similar problem.  I am trying to repartition my hard drive as well.  I have a 45GB fat32 partition for WinXP, and would like to shrink that to 35GB.  The next partition to the right is the ext2 / partition, and the next one after that is the ext2 /home partition.  The very last partition is my 1MB /swap partition, on the far "right".  I used the GParted LiveCD program, and I can shrink the fat32 partition to 35GB by moving the "right" side of the fat32 partition, but I cannot increase the ext2 / partition by moving the "left" side to take over the unallocated space.  All I could do was take a few gigs away my /home partition by shrinking the partition on the "left" side of the /home partition.  After this was done, I can then extend the "right" side of the / partition to cover the unallocated space.  I still want to shrink the fat32 partition and expand the / partition.  How can I do this?
 
I hope this all makes sense!  Thanks!

---

### Post by indytim on 2007-07-02
Assuming you are not bridging between primary partitions and an extended partition, resize your FAT32 partition which will create unallocated space to the right.  After this has been completed, resize the next  partition to include the un-allocated space.  Repeat this process of moving the unallocated space one partition at a time until you get to the end point.

It is my strong recommendation that you NOT bunch your re-sizing tasks in GParted.  In other words, take one complete task and execute it before moving on to the next task.

Hope this helps,

IndyTim

---

### Post by alex_anthony on 2007-07-02
nylecoj813 - what is sda1? is it the dell recovery partition or the utility partition?

---

### Post by rlgoddard on 2007-07-02
> **indytim said:**
> Assuming you are not bridging between primary partitions and an extended partition, resize your FAT32 partition which will create unallocated space to the right. After this has been completed, resize the next partition to include the un-allocated space. Repeat this process of moving the unallocated space one partition at a time until you get to the end point.
 
It is my strong recommendation that you NOT bunch your re-sizing tasks in GParted. In other words, take one complete task and execute it before moving on to the next task.
 
Hope this helps,
 
IndyTim
 
So, what you're saying is that instead of trying to combine two resize operations on one task (one to shrink the FAT32 partition, and the other to expand the / partition to cover the unallocated space), I should just do one resize operation per tasK?
 
I was able to combine two resize operations -- one operation to shrink /home and the other to expand / -- on one task this morning before I left for work (still in progress when I left for work, so I hope it works!).
 
I'll try out your suggestion when I get home from work later today.  Thanks for the tip!

---

