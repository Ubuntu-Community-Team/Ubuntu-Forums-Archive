---
title: "Installation / partitioning problem"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by philipt1969 on 2007-06-21
Hi all

I finally decided to take the plunge and install Ubuntu yesterday, but came across an unexpected problem and I need some advice as to how to proceed.

I was trying to use gparted from the ubuntu live cd to resize the single partition that is currently allocated to windows xp down to 40G (I have a 76.5G hard drive of which 18.5G is currently being used) but for some reason gparted is unable to resize the partition. 

I have also tried to use the guided partitioning from the ubuntu install, but because there is no unallocated space on the drive it cannot proceed with the install.

Any advice as to how I can get around this without having to purchase 3rd party software?

Thanks in advance.

Phil

---

### Post by dptxp on 2007-06-21
Download Gparted, make Live CD, boot with it and try to repartition.

---

### Post by laidback on 2007-06-21
You cannot alter a partition that's active/mounted. Suggest you run the Windoz utility that reorganises your hd before you proceed. Also back up your data/drive.
Then proceed as dptxp suggests, The live version of Gparted is the best in my view and isn't difficult to download and burn.

---

### Post by philipt1969 on 2007-06-21
Using the live cd version of gparted identified a problem with the file system which was sorted running chkdsk from windows.

After sorting that I was able to resize the partition and I now have 35 G of unallocated disk space to dedicate to ubuntu

Now for the next step...setting up the new partitions.

Thanks for the help guys.

---

