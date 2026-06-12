---
title: "Repairing a broken $Bitmap file for NTFS partition"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by joe_aule on 2007-06-18
After my computer crashed during repartioning, windows no longer boots and i cannot finish installing ubuntu. I have been running knoppix for the past few days as it can still access my HD and have managed to rebuild my partition tables using testdisk. I still cannot make make HD mountable in ubunto (liveCD) though.

I have two partitions on my HD, one was added by testdisk which i kept for testing purposes: it was made from the last 708B of my HD and loads fine in with the ubuntu liveCD. The first origional partition does not load in ubuntu though. Syslog says "load_system_files()" failed because $Bitmap could not be loaded. QTparted could not resize the partition and gave the same reason.

All I can find about this file so far is it contains a lsit of which clusters are used, but due to all seach engines ignoring the $ sign i cannot get any info on how to repair the file. If anyone could give me any info or link me to a site where I can download a knoppix (or ubuntu liveCD) compatable install package for a repair tool, I would be most grateful.

---

