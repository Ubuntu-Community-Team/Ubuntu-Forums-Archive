---
title: "Mount/see usb thumb drive?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by velozoom on 2007-09-07
I've been messing with Ubuntu for a while now but am still pretty clueless on device management concepts.  Please forgive the likely stupid questions.  

Ubuntu 7 with a newly purchased PNY 2Gb USB flash drive on an HP dv9000 laptop.  When I insert the drive nothing happens.  I do not see the usb drive listed when I run dmesg nor does there appear to be an entry in the /dev or /dev/media directories.  

Kinda clueless as to where to go from here........forum search didn't help.  Most suggestions I found were to mount something like a /dev/sdd1 but since it doesn't appear Ubuntu won't let me mount a non-existent drive.  ;o)  

Thanks in advance.....

---

### Post by john.nicholls on 2007-09-07
For a start, type ```
sudo fdisk -l 
```in a terminal and see if the drive is listed.

---

### Post by parvinder on 2007-09-07
I'm too new to the device. But usually, if the device is detected by the system it should be there in the Device Manager. 

Did you check in the System->Preferences->Hardware Information if it shows the device?

---

### Post by velozoom on 2007-09-07
$ sudo fdisk -l 
shows only my two HDDs and their partitions.  no thumb drive.

> Did you check in the System->Preferences->Hardware Information if it shows the device?
That was the first place I checked.

---

