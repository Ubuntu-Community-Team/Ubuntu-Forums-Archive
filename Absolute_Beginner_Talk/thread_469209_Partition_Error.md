---
title: "Partition Error"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by federicotedin on 2007-06-09
Ok, so the other day i decided to install Ubuntu becouse Windows isn't working good:(.  I downloaded the iso file and burnt it to a CD.  I booted and i selected install Ubuntu, after this i selected the intall icon in the desktop and followed the wizard.  When i got to the partition part, i didnt know what to do.  I selected the fist option and tried `puting the Partition size slider to 20 GB put i coluldn't (it went from 0.69 to 71 GB), well anways, when i confirmed i wanted to create this partition, it started but then it said there was an error and it aborted, it happened with any way i tried to partition the disk, so if anyone coluld help me i would really appreciate it:).  
Thanx

Ps: also, does ubuntu crate an automatic dual-boot so i can choose an OS when i start the PC?
thanks again
sorry for my english

---

### Post by benerivo on 2007-06-09
Ubuntu does create a dual boot PC, so you get to choose when you switch on. I would go back in to windows and defragment the C drive (keep defragmenting until the process takes only a few seconds). Then reload the ubuntu live cd and open the gparted program from the main menu. Try to resize the main windows partition to make it at least 6GB smaller. If this works then you will have 6GB+ of free space on the drive. Then make two partitions on the free space. Make a 1GB partition of 'swap', and a 5GB partition of 'ext3'.

Open the installer icon on the desktop and choose 'manual' instead of the first option you chose at the partition stage. You can then use the partitions you created to install Ubuntu.

---

