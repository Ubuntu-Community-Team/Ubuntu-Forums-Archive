---
title: "Recommended Partition Plan"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by Hangetsu on 2006-03-15
Hello all!

I've been able to get rid of several applications that were preventing me from moving to Ubuntu, and I'd like some advice on how to proceed.

I have a single hard drive (120GB) that presently has one primary partition of 50GB, with the remaining space unallocated at the moment.  I'd like to create a new partition with 50GB, then a third with the remaining 20.  On that final partition of 20GB, I'll put data files that I want to keep.  So to summarize where were at thus far:

Partition 1:  50GB (NTFS - Windows XP)
Partition 2:  50GB (unformatted)
Partition 3:  20GB (FAT32 - Holds data files)

My concern is that I want to re-partition the two 50GB partitions during the Ubuntu install into six smaller partitions for boot, swap, root, usr, home, tmp, and var.  First, can someone confirm I can do this without destroying my 20GB FAT32 partition (as I don't want to lose that data), and second (if I can do this), can anyone recommend how I should allocate 100GB to Ubuntu?

Thanks much for the help everyone!

---

### Post by TLE on 2006-03-15
Well first of all:
yes you can repartition the first two partitions without destroying the last one. Have a look at [This link]("https://wiki.ubuntu.com/HowtoPartition?highlight=%28partition%29") (Found by going to the wiki and searching for partition)
Regarding partitions, there should be a swap drive that should be twice the size of your RAM. And then you are pretty much free to do what want with the rest. You can allocate it all to just one big root partition / but a more common approach is to also make a /home/  How you wish to split your capacity between these are a matter of how you use your computer. The / is for the operationg system and all the software and /home/ is for all your files, so you should simply split it the way that best suits your needs. i.e. if you want a gazillion application you should make / the larger one, and if you have a lot of e.g. large multimedia files you want in your home folder, then this should be the bigger one. Also check [this link]("https://wiki.ubuntu.com/Installation/I386") It is a install guide and it also contains a section on partitioning.
Happy installing

---

### Post by Hangetsu on 2006-03-15
Thanks for the information, however that leaves me with another open question then:

Given the scenario above, am I OK in that Partition 3 is a Primary Partition at the moment?  In other words, can I have the extended partition before a primary partition?

If I set up partition 3 as an extended partition, will I have to overwrite anything when I resize the primary partitions in front of it?

---

### Post by TLE on 2006-03-17
I'm not really sure, i don't think it is a problem but i'm not sure. I hope someone else can help you

---

