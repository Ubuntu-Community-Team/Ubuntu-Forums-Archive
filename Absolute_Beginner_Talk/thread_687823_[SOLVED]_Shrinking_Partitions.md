---
title: "[SOLVED] Shrinking Partitions"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by leehach on 2008-02-04
Found an interesting thread on shrinking partitions here: [http://ubuntuforums.org/showthread.php?t=683293](http://ubuntuforums.org/showthread.php?t=683293).  One poster comments that it is safer to use the Vista partition manager.  Also, found this note from the LVPM webpage:

> Notes For Vista Users

Vista has its own partition manager, which can be started with the command:

    diskmgmt.msc

It can be used to shrink the NTFS partition to make space for Ubuntu's partition, and may work better than Ubuntu's partitioner. 

I tried to use Vista's partition manager to shrink the Windows partition, and was surprised that on a 500GB hard drive with only 16GB of used space, Vista's partition manager could only find ~220GB of free space.  I intend to try it again with gparted, but I am having monitor display issues during the Ubuntu install (posted in a separate thread).  Would gparted "find" more space than Vista's partition manager?  If it does, is it safe to partition when Vista is finding so little free space?  

I don't really care if I hose the hard drive as it's a new computer and I have the OS and driver CDs.  That said, is there any advantage to using gparted to wipe the drive and install both OSes from scratch?

Sorry for the poorly formed questions, and help will be appreciated.

--Lee

---

### Post by Yes on 2008-02-04
I would try GParted, I imagine it's significantly better than Vista's parition manager.  It's probably ok to use Vista's manager as long as it can see the used space, so you're sure it's not putting that into the new partition.

I can't see why you would wipe the drive and install them both from scratch.  If for some reason you do, remember to install Windows first, I hear it's a pain to install it after Ubuntu.

---

### Post by Superkoop on 2008-02-04
You should consider yourself lucky that Vista found that much of your HDD. When I was trying to use Vista's partition manager it would only give me 2GB. 
So just go ahead and use Gparted from the live CD, it works way better. And it gave me all the space I wanted. 
Gparted > Vista's partition manager
^_^

---

### Post by dogerelly on 2008-02-04
I had a similar problem with Vistas partition shrink--very small amount of space found. However, after defragmenting the hard drive in windows much more was available, GParted may well be better, but I felt I wanted to shrink a windows partition with a windows program as illogical as that may seem....

---

### Post by leehach on 2008-02-04
Thanks for the feedback.  Dogerelly, I did do a defrag after the finding so little space, although for a completely new computer I would have been surprised for the disk to be very fragmented.  After the defrag, Vista's partition manager didn't find any more space than before.

---

### Post by Superkoop on 2008-02-04
Yeah I had defragmented my hard drive too, and I didn't get anymore than before. You just need to use Gparted if you want to be able to really get what you want. A quick google search showed that a lot of people have the same problem. (Not suprising though, it's Vi$ta)

---

### Post by leehach on 2008-02-05
OK, I ran gparted (or rather, I'm running the resize right now) and it found all the space.  I'm setting up partitions for Vista, Ubuntu, swap, and data (what will become /home).

Interestingly, I think I found out what's going wrong with the install, because the screen went blank the first time I ran gparted, but I tried it again and this time used the option to force VESA, and the screen didn't die.  Now I just have to figure out how to force VESA during a Ubuntu install.

Thanks for the help.

---

### Post by leehach on 2008-02-05
Final note for whoever is interested.  First time booting to Vista after partitioning, the OS failed to load and the computer rebooted itself.  On reboot, it automatically went into chkdsk.  Found 4 unindexed files, repaired the disk, rebooted again, and successfully loaded.

Now I just have to install Ubuntu on the partition I created!

Thanks for you help and comments!

---

