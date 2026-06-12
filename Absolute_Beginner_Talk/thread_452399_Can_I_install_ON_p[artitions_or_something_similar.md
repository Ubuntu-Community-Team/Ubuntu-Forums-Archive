---
title: "Can I install ON p[artitions or something similar?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by nintennuendo on 2007-05-23
I have a 70gb hd at work and I want ubuntu on it as a dual-boot.  I made 16gb for the Windows installation, and the rest i put for data, music pictures games etc.  Can I set aside another 16 from that partition and make that for Ubuntu?  I have Partition Commander 10 for windows, i don't know if Ubuntu could partition that partition.

---

### Post by seshomaru samma on 2007-05-23
What you should do is part your disc like this 
first partition (NTFS) - Windows (what in the Windows world is called "C:")
second partition (FAT32) - Data and files - which both Linux and Windows can read and write to (Linux doesnt handle NTFS very well)
third partition (Ext3) - Linux
forth partition swap - this is a small partition needed for Linux ,usually twice the size of your RAM

the Ubuntu installer comes with a partition programme which is very good
however ,Linux does not refer to partitions as C, D or E , so if you are used to Windows you might find it confusing at first.
What I would suggest is using your Partition Comander to part your disc, you can leave the space you design for Linux as unpartitioned , the Ubuntu installer will format it as Ext3 and automatically create the swap partition.
During installation choose the option of 'use the largest unformated space'
or you can choose 'manual' and create an EXT3 partition out of the unallocated space yourself.


also before installing , i suggest reading [this link ]("http://www.psychocats.net/ubuntu/")carefully ,especially the 'just beginning' section on the right hand side.

---

### Post by drowner on 2007-05-23
> **nintennuendo said:**
> I have a 70gb hd at work and I want ubuntu on it as a dual-boot.  I made 16gb for the Windows installation, and the rest i put for data, music pictures games etc.  Can I set aside another 16 from that partition and make that for Ubuntu?  I have Partition Commander 10 for windows, i don't know if Ubuntu could partition that partition.

You COULD use partition manager, but there's kind of no need.

The Ubuntu installation can partition it for you.

Either way should work fine.

Just make sure, if you want to dual boot, that you don't let ubuntu write to the whole hard drive, you need to choose the manual partitioning step.

You'll know it when you see it ;)

Oh, and defragment first.

---

