---
title: "my experiences installing ubuntu and xp with 2 hard drives"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-07
I hope the following will help somebody install windows xp and ubuntu onto a computer with two internal hard drives.

I think that I have read too many articles about formatting drives and tried to complicate matters by formatting with NTFS, FAT32, EXT3 and swap files galore.  

Over the last 48 hours I have learnt to simplify matters and let the instilation process make all the decisions for me.  

On my master drive I shrank the Windows partition to 20gb and formatted the rest of the free space to FAT 32.  On my slave drive I simply formatted my free space into FAT 32.  Once I had done this I ran the Live CD and followed all the recomended options and this made for a relatively pain free experience. 

Unexpectidly the instilation created all the necessary partitions on the slave drive and not the master drive, as I was expecting with my experiences of dual booting Windows Vista.  I wasted a lot of time trying to get my master drive ready for instilation when all along ubuntu wanted to work on my slave drive.  

When I had installed ubuntu for the first time and booted up for the first time I learnt that the boot-up sequence would stall.  I simply hit the Off Switch and switched the computer on a couple of times untill the system finally booted up.

I then powered down the computer so that I could boot up into XP.  The first attempt would fail and send me back to the initial GRUB screen where I chose which OS to install.  And when I re-tried to boot XP I would be given the option to boot in safe mode or carry on.  After tryal and error I lernt to continue to boot normally.  This would unexpectidly boot up ubuntu.   I would then have to power down and re-boot into XP, which, thankfully would power up sucessfully.  From then on, I could sucessfully boot into either system from the GRUB screen.  I have now done this enough times to understand that, for me, is a normal way to get the computer to learn to dual boot.

We all live and learn.

I hope that my experiences will help somebody else in the same situation of installing ubuntu and XP onto a computer with two internal drives.

---

### Post by bulldog on 2007-05-07
Nothing wrong with your story :) 

But as a side note,there are users who want some more grip on the install procedure.
They want a /home or a separate /data partition,so when they want to do a fresh install,their data is relative safe.
But if you just want to check out ubuntu,and not putting any important data in ubuntu,you can let the installer and partitioner do all the work for you.

---

### Post by the lemming on 2007-05-07
> **bulldog said:**
> Nothing wrong with your story :) 


But if you just want to check out ubuntu,and not putting any important data in ubuntu,you can let the installer and partitioner do all the work for you.


I agree.  I read too much and tried to partition this, that and the other.  All I should have done was let the installer do all the hard work.

---

### Post by starcraft.man on 2007-05-07
> **bulldog said:**
> Nothing wrong with your story :) 

But as a side note,there are users who want some more grip on the install procedure.
They want a /home or a separate /data partition,so when they want to do a fresh install,their data is relative safe.
But if you just want to check out ubuntu,and not putting any important data in ubuntu,you can let the installer and partitioner do all the work for you.

Strongly second the home partition, I tell all the people I help to make it. Its a pain to move around/resize paritions to get home in later when they find out they like Ubuntu :p.

Glad ya got it working though, once Ubuntu is set up though its a breeze to do anything, with no need for maintenance :)

---

