---
title: "partition windows disk to accomodate linux"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Jbirdie1 on 2006-07-10
my plan is to use partition magic under windows to slice off a 30gb chunk of my current disk and create it with ext3. the reason for this is that i dont know anything about how this gparted works and dont want to zero out everything. upon install of dapper drake i plan to let the linux installer/partitioner decide how to divy up the 30gb and what file system it needs. is this a sound plan?? i dont want to initially use a linux partitioner simply because i dont know anything about it...

---

### Post by aysiu on 2006-07-10
You know what I'd do?

I wouldn't install Ubuntu just yet. Use the live CD for a week or two. Get *really* comfortable with Ubuntu.

Then think about how to partition it.

Some helpful links:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by michael1977 on 2006-07-10
Sound advice as usual aysiu.  However, if you are at all like me who just dove into linux at the most inopportune time because I was antsy and impetuous (i.e. in the middle of writing a thesis) your plan sounds fine the installer should see both of your patitions and just tell the installer to play with the one that does not have windows on it, the installer will format and divide the space for the system and the swap etc.  The other method is a little more simple because you merely use the ubuntu installer instead of partition magic.  The installer will read your drive show you your ntsc partition ask if you wanna make enough free space and ask how much.  My caution with this method is merely this; if you are not familiar with linux and have never used a partitioner under linux even though Ubunut's is rather simple and user friendly, you may wanna stick with your original plan because it sounds like you know what you are doing regarding that particular program.  Honestly I have never used ptmagic and wouldn't know where to start so it usually is best to go with what you know, especially if you are just starting out with linux.

---

### Post by molly_001 on 2006-07-10
> **Jbirdie1 said:**
> my plan is to use partition magic under windows to slice off a 30gb chunk of my current disk and create it with ext3.

Bad idea, says me.  GParted is very easy and intuitive to use.  If you can slide a slider bar, you'll be done with the whole task in 1.3 seconds.  GParted can resize the NTFS partition, and insert ext3 partitions.  

You were close to a best plan of action (in my opinion) from the start, though: Use Gparted to merely shrink your NTFS partition by a size of 30GB.  _Leave it as unpartitioned space_.  Then reboot and let Windows satisfy itself  (takes about five minutes) that the resizing did not corrupt the Windows install.  (It won't corrupt a thing.)  

Then when you use the Ubuntu LiveCD installer, it will give you a nice, sweet option of "Install Ubuntu into the largest unformatted space."  You click that option, and the installer handles the rest.  Your NTFS partition remains the same (albeit shrunk according to your command earlier).  And the installer will put your Ubuntu ext3 partition, a tiny Memory Swap partition (necessary) -- and voila!  You are done and ready to dual boot.

Of course, before doing any of the above, you will make a 100% backup of any data on the Windows partition that you wish to keep.  Right?!

---

