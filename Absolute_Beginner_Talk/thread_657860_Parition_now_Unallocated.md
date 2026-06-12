---
title: "/ Parition now Unallocated"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by crav on 2008-01-04
cutting out the back story and getting straight to the problem:

My main partition, the one that held Ubuntu, my home folder, and everything else linux related is messed up. Loading up the GParted LiveCD and it shows that partition as unallocated space.

I'm not looking to get the whole partition back, I understand how difficult that might be. Is there any way for me to at least get my home folder and my evolution mailbox back?

Please help! I'm totally cut off and had to resurrect an old Win2K machine just to post this!

---

### Post by ~LoKe on 2008-01-04
Back story is necessary.  What did you do to cause this?  Did you format the partition?

---

### Post by crav on 2008-01-04
I went the wrong way in the windows install cd (wasn't trying to get rid of Ubuntu, I promise!) and started formatting. I cut power after 5-10 seconds, when I'd realized what was happening. It would seem to me that the most damage that could really be done is messing up however many files can be formatted over in those 5-10 seconds.

---

### Post by zipperback on 2008-01-04
> **crav said:**
> I went the wrong way in the windows install cd (wasn't trying to get rid of Ubuntu, I promise!) and started formatting. I cut power after 5-10 seconds, when I'd realized what was happening. It would seem to me that the most damage that could really be done is messing up however many files can be formatted over in those 5-10 seconds.

It would seem that the problem is that you allowed windows to delete the partition information.

I don't know of any way to restore the partition since windows had already over written the partition information and proceeded to format the partition.

I would consider it a hard lesson that you've learned from this, and reinstall Ubuntu.

Then restore your data from backup. You DID make a backup before all this RIGHT? 

- zipperback
:popcorn:

---

### Post by ~LoKe on 2008-01-04
Formatting a partition is a good way to make data unrecoverable.  I'm almost positive you can't get it back.

---

### Post by crav on 2008-01-06
one last attempt before i reformat...

---

### Post by Moop on 2008-01-06
You might be able to recover your partition with Testdisk. It's worth a shot. 

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

