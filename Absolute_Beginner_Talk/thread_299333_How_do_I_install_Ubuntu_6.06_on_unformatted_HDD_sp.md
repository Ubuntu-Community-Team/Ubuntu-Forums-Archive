---
title: "How do I install Ubuntu 6.06 on unformatted HDD space?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by jacatone on 2006-11-14
I've already allocated 10 gigs of open space from my Windows XP partition for Ubuntu. But when I try to install Ubuntu it sees that space but then asks which partition I want to use for the install and only shows hda 1 and hda 5 which are my Windows partition and a backup partition. Doesn't it allow you to pre-partition your HDD for installation? Also, what is Primary and Logical drives and what is a swap file? Thanks.

---

### Post by K.Mandla on 2006-11-14
Make sure the space you want Ubuntu to take up is unpartitioned too. It's not enough that it's not formatted. If the partitioner sees a partition in a space, it thinks it's taken up by something else, and won't try to use it. 

You can remove a partition from your drive from within Windows, if you're comfortable with that. Right-click on My Computer, pick Manage, then Disk Management. It'll show the partitions and right-clicking on those will give you the option to delete it.

It uses hda1 and hda5 as the default partitions. There's [a great explanation of primary and extended partitions and logical drives]("http://en.wikipedia.org/wiki/Disk_partitioning") on Wikipedia.

The partitioner creates hda1 to hold your Ubuntu system files and your personal documents -- your "home" folder. A swap file is like a paging file in Windows -- it's extra space for the system in case it runs out of memory.

By the way, did you back everything up before you started to install?

---

### Post by jacatone on 2006-11-14
I think your right. When I opened Disk Management it's just showing C drive and my backup drive. I created this space with Partition Magic 8.0, and it just shows it as extended space I took from C drive. Know how to remove it in Partition Magic? Thanks.

---

### Post by Mohit on 2006-11-14
when u start installation process it will ask whether
1 manually partition the memory
2 large contineous memory
3 format the Hdd

just use large contineous memory space


this will work

---

