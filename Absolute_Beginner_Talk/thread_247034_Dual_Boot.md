---
title: "Dual Boot"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by eisle89 on 2006-08-30
Hello all, I'd like to ask for some help setting up my install. I am running WinXP64 on partition C: (8gig) and storing data on the partition D: (65 gig). How do I setup ubuntu on my partition D: and retain my Windows data files ?? TIA

---

### Post by TFX360 on 2006-08-30
> **eisle89 said:**
> Hello all, I'd like to ask for some help setting up my install. I am running WinXP64 on partition C: (8gig) and storing data on the partition D: (65 gig). How do I setup ubuntu on my partition D: and retain my Windows data files ?? TIA

Read up about how to resize a partition:


[http://gparted.sourceforge.net/documentation.php]("http://gparted.sourceforge.net/documentation.php")

Boot via the live CD

Open System / Administration / Gparted


And resize your partition.

---

### Post by thorium on 2006-08-30
Divide partition D: into two partitions by “PowerQuest PartitionMagic”.Then delete the one that is empty. Now you can setup install ubuntu.

You aslo can start ubuntu on vmware workstation.

Sorry for my poor English.

---

### Post by eisle89 on 2006-08-31
Thanks TFX360, that did it

---

### Post by TFX360 on 2006-08-31
> **eisle89 said:**
> Thanks TFX360, that did it

Your welcome, thanks for the reply! Lets me know it helped!

---

