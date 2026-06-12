---
title: "Partitioning question; (installing over FC5)"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by sadscientist on 2006-07-10
Hi :)  

I have Windows XP and FC5 installed on a single hdd.  I want to overwrite the FC5 installation with ubuntu.  I had used PartitionExpert to rearrange my partitions.. hda had a 120gb ntfs partition, 2 gb swap, and about 40 gb of unused space.  During the install of fc5 I let anaconda use the unused space and automatically do its thing.

I downloaded the ubuntu server install iso, but I'm a little confused at the partitioning stage:  I don't want to use partitionexpert to erase the partitions fc5 is now occupying.. (this would screw up my bootloader, I think).  I also don't want to format the entire hdd during the ubuntu install.  (I want to keep the ntfs partition).  One odd thing fc5 did was create one small (~100mb) ext3 partition and one larger (~39gb) lvm partition.  

So, my question: how do I tell ubuntu's installer to format only the ext3, and lvm partitions, join them into a single ext3 hda2, and stick ubuntu in there?

---

### Post by sadscientist on 2006-07-10
I found the "Installation and Upgrade Help" forum, hah.  Sorry.  I'm assuming there are similar threads there..

---

### Post by sadscientist on 2006-07-10
I hate leaving threads without conclusions, soo..

I'm going to use PartitionExpert to repartition hda1 to full-sized 160gb ntfs partition, then follow [these instructions]("http://psychocats.net/ubuntu/installing.html") to shrink the partition and plop ubuntu in.  (thanks for the link RRS)

---

### Post by sadscientist on 2006-07-17
Haha that got me into a horrible mess. (basically, Ubuntu's installer "couldn't" shrink the ntfs partition after I'd enlarged it to 160 gig .. so I couldn't boot to windows since the mbr had grub in it, and I couldn't boot to linux since I'd overwritten its partition.) 

In the future, when I want to install over-top of a linux partition without formatting the entire hdd, I will use PartitionExpert to remove the ext3 and swap partitions, and "Use free space" during the next linux install.  :)

i.e. There's no point in enlarging the ntfs partition so that it consumes the entire hdd.

---

