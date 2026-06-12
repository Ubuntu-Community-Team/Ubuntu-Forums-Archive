---
title: "Dual booting question"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by cremnob on 2005-10-13
Hi I'm thinking of dualbooting with Ubuntu but I can't seem to find any tutorials or guides that will show me how to set up the partitions etc.

I have 1 200gb hard drive with 2 NTFS partitions on it. C: is about 50gb and E: is about 85gb. I'm thinking of trying to make the partitions needed with PartitionMagic. What I want to know is will PartitionMagic be able to do the job. And would I select Linux in it and then EXT2? How big should the swap partition be? I just dont want to mess something up with my Windows partition. :???: 

Thanks :D

---

### Post by gflores on 2005-10-13
Very first thing you should do is backup any important data you may have... just in case. 

If you have free space that you are not using, you do not have to use partitionMagic. From what I can tell, you're only using 135 (50+85). The Ubuntu installer will do the partitioning for you in this case. Just do guided installation and you'll be fine.

Swap is generally twice your memory amount, but typically between 512mb to 1GB. 

Lastly, I would suggest you use ext3 as you filesystem instead of the older ext2.

This might help.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

