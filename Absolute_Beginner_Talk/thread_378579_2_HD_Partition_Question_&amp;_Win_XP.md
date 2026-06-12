---
title: "2 HD Partition Question &amp; Win XP"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by lkeffect79 on 2007-03-07
I have 2 40GB IDE hard drives. I want to load Ubuntu on the master as my primary OS and install XPhome on the slave drive so I can dual boot to play games. 

The master drive had a win2k NTFS partition but I plan to format for Ubuntu.

The slave drive is currently a single NTFS partition with ~30 GB of docs/music/movies/archives that I need to keep and no OS.

In addition I would like to be able be able to exchange files between the two OS's, mostly sending from ubuntu -> XP, but I would also like to grab files from the XP partition.

Would somebody recommend some  good partition schemes for me? I plan on loading Ubuntu first, moving files from the NTFS drive to ubuntu, and then installing XP on the 2nd drive. 

Thanks

---

### Post by fdrake on 2007-03-07
what i can suggest is to save your data on your windows hd(master) and free the slave hd reformat it and install ubuntu on it. I don't think you can move your windows installation to the slave hd without deleting your data.
Anyway , you can  browse and move data between the two hd after ubuntu is being installed.
it won't matter in which hd (slave or master) you installed your ubuntu or windows systems. you can still dualboot them.To do this you'll need also to change your bios setting so that the slave HD is being booted before the master.

---

### Post by Carnavan7 on 2007-03-07
All Id want to add to the above is that its usually easier to install xp first, then linux, as xp doesnt play nicely with the master boot record etc. Good luck with it :)

---

### Post by lkeffect79 on 2007-03-07
It sounds like it is easier to install windows first, and then ubuntu for a dual boot system.

So do a fresh install of XP on the master drive first, copy data over from the slave, and then install ubuntu on the slave? There is no upgrade path from win2k -> XPhome (f***** M$) So I have to wipe the old master and install XP. 

In the end I want most of the data currently on my XP HD to be in the ubuntu partition. I don't want or need an especially large (>20 GB) XP partition and I want ubuntu as my primary startup OS. When I install ubuntu what would be the best way to partition to achieve this?

---

### Post by lkeffect79 on 2007-03-07
So when installing XP it completely overwrites the old master boot record?

I did a half-assed install of ubuntu last night on the master HD and was wondering if it is a problem to install XP on top of it?

---

### Post by dstew on 2007-03-07
Why not install Windows XP on your first drive, then repartition and install Ubuntu linux also on the new partition of the first drive? At installation of Ubuntu, install grub to dual boot the first drive. Then leave your second drive untouched.

And yes, if you install windows over ubuntu, it wipes out your MBR. If you think the ubuntu installation is intact, but unbootable, you can try to install grub, but you have to get it from another disk, like a live CD or a grub bootable floppy.

---

### Post by fdrake on 2007-03-07
or you can resize  the partition with your data in the  second hd and install ubuntu in it using the free space ?20GB more then enough for ubuntu.

---

### Post by lkeffect79 on 2007-03-07
> **dstew said:**
> Why not install Windows XP on your first drive, then repartition and install Ubuntu linux also on the new partition of the first drive? At installation of Ubuntu, install grub to dual boot the first drive. Then leave your second drive untouched.


Thanks! That sounds like the best plan of attack. A question I still have is that the second drive will still be NTFS. Does using ntfs-3g more or loss work seamlessly? Plus is there a way to access linux partitions from XP?

I'm thinking the drives would look a little like this:

Master:
20GB WinXP - NTFS
20GB linux - I need recommendations on the best setup for this. Is the standard install best?

Slave
40GB - NTFS

---

### Post by fdrake on 2007-03-07
[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)

---

### Post by fdrake on 2007-03-07
yes you can access linux partition in windows [http://news.softpedia.com/news/Access-Linux-partitions-files-under-Windows-48292.shtml](http://news.softpedia.com/news/Access-Linux-partitions-files-under-Windows-48292.shtml)

---

### Post by fdrake on 2007-03-07
> **lkeffect79 said:**
> 
Master:
20GB WinXP - NTFS
20GB linux - I need recommendations on the best setup for this. Is the standard install best?
[http://www.hezardastan.org/breezy_xp_dualboot/en/](http://www.hezardastan.org/breezy_xp_dualboot/en/)
hope this will help:)
Check this video ..
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

---

### Post by lkeffect79 on 2007-03-07
Thanks for all of your help! I'll see how it goes in a couple of hours when I get off of work. Course It'll take like 2 hours to load XP and 45 minutes to get Ubuntu installed. :)

---

