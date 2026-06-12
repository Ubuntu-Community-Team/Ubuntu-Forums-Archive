---
title: "NTFS has to be erased"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by JerseyDevil1111 on 2008-01-29
How do I install Ubuntu on a NTFS partition? How do I erase the NTFS and have unallocated space for Linux?

---

### Post by pebo on 2008-01-29
Try [this]("http://www.psychocats.net/ubuntu/partitioning") tutorial. You can partition your drive from the install cd. You will have to format the file system to a linux compatible one.

---

### Post by randy78 on 2008-01-29
You could install Ubuntu on an existing Windows installation through a program called Wubi ([http://wubi-installer.org/](http://wubi-installer.org/)) and that will allow you to demo Ubuntu and not have to make any changes or any long term commitments.

As far as installing Ubuntu on an NTFS file system, I'm not sure that you can.

Linux uses its own file systems (Ext2, Ext3, Reiser, etc...).

You could boot up the live cd, go to System>Administration>Partition Manager (I think that's what it's called) and then you can click on the NTFS partition, delete it and then re-format the free space into a Linux file system.

However, once you do that and commit to the changes, there is no turning back, so be 100% sure that this is what you want to do!

Hope this helps

---

### Post by njparton on 2008-01-29
Have a look at Wubi (google it).

Otherwise you'll have to remove the NFTS filesystem and re-format it with a linux equivalent, this can all be done via the installer at the partitioning stage.

---

