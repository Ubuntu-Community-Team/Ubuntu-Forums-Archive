---
title: "Gparted live CD not working for partitioning"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by kidob on 2007-06-13
I was unable to partition my hard drive using the alternative installation CD so now I'm trying to do it with the Gparted live CD but so far this isn't working either. 

I actually had to re-install XP because my last attempt at partitioning messed up my Windows system. When I re-installed I formatted only the first 15 GB on my 40 GB drive, and left the rest empty for Ubuntu. But gparted won't let me do anything with this space. When I pull down the "partition" menu for the empty space, only the "Resize/Move" option is clickable, the "Format to" option is not accessible. When I select Resize I can't do anything with that either because the minimum and maximum amounts for the new size are identical, namely 23156 MB, which is the entire space. It also says that the free space preceding is 0 MB, which is odd. What's going on? Maybe I should just try to partition with the installation CD. Since this time I don't have to re-size Windows maybe it will work, but after a long 2 days and still no partitioning I'm none too optimistic. Please help!!!  :(

---

### Post by confused57 on 2007-06-13
> **kidob said:**
> I was unable to partition my hard drive using the alternative installation CD so now I'm trying to do it with the Gparted live CD but so far this isn't working either. 

I actually had to re-install XP because my last attempt at partitioning messed up my Windows system. When I re-installed I formatted only the first 15 GB on my 40 GB drive, and left the rest empty for Ubuntu. But gparted won't let me do anything with this space. When I pull down the "partition" menu for the empty space, only the "Resize/Move" option is clickable, the "Format to" option is not accessible. When I select Resize I can't do anything with that either because the minimum and maximum amounts for the new size are identical, namely 23156 MB, which is the entire space. It also says that the free space preceding is 0 MB, which is odd. What's going on? Maybe I should just try to partition with the installation CD. Since this time I don't have to re-size Windows maybe it will work, but after a long 2 days and still no partitioning I'm none too optimistic. Please help!!!  :(
Maybe I'm missing something, but have you tried create new partition...then you "should" be able to create a new partition to the size you want...otherwise, I'm not sure what the problem might be.
Is the space shown as "unallocated", or is it showing a formatted  filesystem in the gparted live cd?

---

