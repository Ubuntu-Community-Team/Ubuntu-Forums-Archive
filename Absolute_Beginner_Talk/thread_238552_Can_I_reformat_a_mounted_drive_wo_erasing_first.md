---
title: "Can I reformat a mounted drive w/o erasing first?"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by johnnyboy on 2006-08-17
My partitions are:

/dev/hda1 - ext3 filesystem - 54.5GB total, 5.7GB used
/dev/hda2 - extended filesystem - 1.44 total, 0 used
/dev/hda5 - linux swap filesystem.

Obviously almost the entire hard drive is on hda1.  Can I repartition to create another partition for the windows system WITHOUT erasing my harddisk prior to?

---

### Post by hopstah on 2006-08-17
yes, but it's always a good idea to backup all important data first.

download the ubuntu live cd and boot into it and begin the install process again.  there will be a point when you define the partitions, and it's at that point that you can resize and create partitions.

search the forums for howto threads about gparted

---

### Post by johnnyboy on 2006-08-18
thanks.  I have a copy of live, so at least that much  is accomplished ;).  I actually already downloaded Gparted, however I cannot repartition any of the drives.  The only options I have are to reformat (which erases all data) and unmount.  However I'm nervous about unmounting as I'm not sure if it may disallow access to my OS.

---

### Post by bodhi.zazen on 2006-08-18
If you in the GParted CD:

Unmount the hard drive. You will then be able to resize, etc.

If you want you can remonut at any time but you will likely just boot to Unbutu and install.

---

