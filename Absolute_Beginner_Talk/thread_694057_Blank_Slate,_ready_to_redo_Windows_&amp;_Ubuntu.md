---
title: "Blank Slate, ready to redo Windows &amp; Ubuntu"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by ChaOConnor on 2008-02-11
Good day!  Here is what I have: 320Gig SATA Pri, 500Gig SATA Secondary hard drive.

I'm going to blow everything away and start fresh.  Currently I have Windows XP & Ubuntu.  

What I need:
Ubuntu as primary OS
XP for small use (iTunes store, some games, etc.)
General Storage for music & movies
Swap Space

So what do you think is the best distribution & file format for my setup?  I'm thinking the whole 500 gig secondary is the General Storage drive, but what do I make it?  NTFS, FAT32, etc.?

Any help you can provide is greatly appreciated!

---

### Post by spiderbatdad on 2008-02-11
You might check out this how-to:[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by ChaOConnor on 2008-02-11
Thank you!  I had read that article and that's good info I'll use, but I guess I was looking for more what people suggested, size and partition wise... The steps to make it happen I'm cool with, I guess I wonder what people have found to be sufficient/work for them.  Thanks though for the info, I appreciate it!

---

### Post by Zed on 2008-02-11
First, boot the Ubuntu installation CD and do your partitioning. Windows will be the first partition (it gets cranky if it's not first.) Give it something like 30-80 GB, depending on how many games you might be using. (I run it comfortably in a 25GB partition, but I don't have much added software.) Make the swap partition next. The usual advice is to make it twice the size of your RAM. Then let the rest be your ubuntu root, formatted ext3. (Other filesystems might offer better performance under particular circumstances, but I suggest going with ext3 if you don't have a specific reason for one of the others.)

Now get out of the installation and install Windows in that first partition. (Windows' own partitioning tool is a pain.) (The only part you really had to do before installing Windows is creating a first partition of the right size -- you could leave the other partitions till later if you wanted.)

Reboot the Ubuntu CD. Give it a mount point for the first partition. I use /xp; I think it'll offer /media/windows as one of the choices. Make sure it doesn't reformat it. Tell it again that swap is swap and that the big ext3 partition is your root directory. Finish the installation.

[This article]("http://www.linuxjournal.com/article/8761") suggests using FAT32 for a filesystem for shared access on a Windows-linux dual-boot system. You could use ext2 and install ext2 drivers on Windows. Linux can read NTFS just fine, but last I knew, writing wasn't recommended (this may have changed, though.)

---

