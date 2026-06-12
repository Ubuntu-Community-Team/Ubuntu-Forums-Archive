---
title: "Partitioning problems on install."
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by PlayWithFire on 2006-06-29
I want to try to force myself to start using linux, mainly to be familiar with another OS. 
Well, i can't even start installing it, and the step that i get stuck on, is the repartitioning part. First, i tried just doing nothing and letting Ubuntu resize the partition. It just hung there for a while, so i canceled, rebooted, and decided to just create a 50GB of unpartitioned space with PartitionMagic. Well, i can't seem to be able to do that. It errors out with error 1592. Ubuntu, when it tries to reparition either gives an error, or just hangs there. 

I know i should provide the text of the error messages, but sorry, i forgot to write them down, and i am now at work.

---

### Post by bohboh on 2006-06-29
Are you trying to install it onto a SATA hard drive?

---

### Post by PlayWithFire on 2006-06-29
yes, i am
why does it matter?

---

### Post by bohboh on 2006-06-29
Yes. I had a sata hd which did exactly the same. It would hang on partitioning. I tried alsorts and in the end had to concede defeat and install on an ATA hd.

I read and tried loads, i never really found a reason BUT it has something to do with poor support for sata drivers. What, i dont know. The annoying thing was that it would work ok for others.

To test i installed FC5 on the SATA disk and it installed ok. So its an ubuntu issue with SATA disks. If you find a solution then post it, i am sure there are others with the same problem.

[Tried this]("http://ubuntuforums.org/showthread.php?t=201618&highlight=sata+hangs")

Are you installing from the very latest version?

---

### Post by PlayWithFire on 2006-06-29
well, i guess i could try to clean out some space on my external drive, and install it there, but it's not my first choice. If anyone figures out a way to help, please let me know
Thanks!

---

### Post by Apple 101 on 2006-06-30
Use the SATA drive... my works perfectly by the way...

Anyway, use Partition Magic to create the 50 GB space you wanted by resizing the partition.
In the Linux installer, partition that now free 50 GB space.  That should work.

---

