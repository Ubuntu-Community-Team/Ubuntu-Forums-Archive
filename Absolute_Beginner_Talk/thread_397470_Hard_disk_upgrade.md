---
title: "Hard disk upgrade"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Xkutzy on 2007-03-30
I have a PC that I have put together from parts to try Ubuntu. I like what I see, so I now want to convert this to a more usable machine. My main problem is hard disk space. I have two slow 6Gbyte IDE drives, one with Windows 2000, and one with Ubuntu Dapper. I have bought a newer 80Gbyte disk, and want to use it to replace both smaller drives. So what is the best method to use to do this. I do need to dual boot. I don't want to re-install from scratch as this takes too long. I have at my disposal a 250Gbyte USB drive. The PC has a CD writer. I have a copy of Norton Ghost somewhere, and a copy of partition magic.

Any thoughts?

---

### Post by wonk-o-matic on 2007-03-30
Is your Windows partition NTFS or FAT32?

---

### Post by Xkutzy on 2007-04-02
(Apologies for the delay in replying. Real life intervened!)

Windows HD is NTFS.

---

### Post by linuxjerk on 2007-04-02
I've been fighting this for what seems like weeks. There is no utility to copy your installation to your new hard disk. I can't believe you have to reinstall to move to your new disk. :confused:

---

### Post by wonk-o-matic on 2007-04-02
Ah, yes, the joys of Windows.  I've been through this a number of times, and I get a bit frustrated, too.  Many other OS's will just let you partition/format/copy to your new drive, but Windows is always a bit more interesting.  

If your new drive didn't come with a utility disk, and you don't have any method to do a full backup with restore, you can use a Linux live-cd to rescue things.  My own personal favorite is the method is here:

[http://alma.ch/blogs/bahut/2005/04/cloning-xp-with-linux-and-ntfsclone.html](http://alma.ch/blogs/bahut/2005/04/cloning-xp-with-linux-and-ntfsclone.html)

It's a method I've used several times.  I massage it a little to get the partitions exactly the way I like, and I don't compress anything.  I have questions about how the internals of ntfs will handle new clusters (if you increase the drive size) and bad sectors, but overall, it does what I need.

---

### Post by insane_alien on 2007-04-02
dd_rescue can copy the drives block by block. use that.

---

### Post by wonk-o-matic on 2007-04-02
Yes, dd_rescue can be useful.  You probably want to copy the partition, rather than the whole drive.  Otherwise, you will end up with the partition table from the old drive, and you probably don't want that.  So, /dev/hda1, rather than /dev/hda, assuming that the old drive is the first drive.  

Isn't it ridiculous that you have to go to these extremes just to move Windows to a new drive?  My efforts continue to eradicate it from my house.

---

