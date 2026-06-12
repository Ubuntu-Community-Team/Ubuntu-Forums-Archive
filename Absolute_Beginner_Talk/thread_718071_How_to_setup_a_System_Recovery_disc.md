---
title: "How to setup a System Recovery disc"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by kcav45 on 2008-03-07
Please advise best way to setup a recovery disk for "Gutsy Gibbon" to be installed on Seagate, Momentus, 5400 hard drives.

Have Ubuntu 7.10 running from Livecd.  Both the internal hard drisk drive, and CD/DVD burners are accessible from Ubuntu.  I plan to: 
(1)  make an image file of the present disk 
(2) burn the image file to a recovery disk 
(3) repartition the disk for "Gutsy Gibbon" and format each partition 
(4) restore the system from the recovery disc to its present state.  
Just to prove I can do it.  :)  Then repartition before installing " Gutsy Gibbon".   

I have LGE, Super Multi DVD Rewriter that is Light Scribe enabled but it does not have Blu-ray.  And Seagate, Momentuse hard drives, 60GB and 160GB capacities.   What utility should I use for imaging?  How should I prepare the recovery disk?  Should it include utilities for repositioning disk partitions, analyzing the disk for defects, encryption, compression, etc.

KC

---

### Post by JoshuaRL on 2008-03-07
I would suggest [Remastersys.](http://www.remastersys.klikit.org/)  I haven't used it myself, but I've heard it works pretty well.

---

### Post by kwacka on 2008-03-07
I like partimage - its in the universe repository.

Homepage at: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)   

includes the blurb "For example, if you buy 50 PCs, with the same hardware, and you want to install the same linux systems on all 50 PCs, you will save a lot of time. Indeed, you just have to install on the first PC and create an image from it. For the 49 others, you can use the image file and Partition Image's restore function." 

It only copies data - not unused sectors, can compresses the file & write across multiple disks.

---

