---
title: "How would I partition my external harddrive in Gutsy?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-04
How would I partition my external harddrive using Gutsy? It's a 250GB vfat. Could I dual boot off it?

---

### Post by Pumalite on 2007-11-04
[http://ubuntuforums.org/showthread.php?t=598961](http://ubuntuforums.org/showthread.php?t=598961)
I don't know about dual booting off it.

---

### Post by Steven_B on 2007-11-04
Yes to all of the above.  You have to be a little careful, but it isn't too difficult.
Use GParted to modify the partitions.  When you open it, select your external drive from the drop-down menu in the upper-right corner.  You can then edit the partitions like any other hard drive.

Are you trying to dual-boot multiple operating systems from your external drive, or are you wanting to leave one OS on your internal drive and put Ubuntu only on your external?

---

### Post by 449 on 2007-11-04
> **Steven_B said:**
> Yes to all of the above.  You have to be a little careful, but it isn't too difficult.
Use GParted to modify the partitions.  When you open it, select your external drive from the drop-down menu in the upper-right corner.  You can then edit the partitions like any other hard drive.

Are you trying to dual-boot multiple operating systems from your external drive, or are you wanting to leave one OS on your internal drive and put Ubuntu only on your external?

Right now Ubuntu is on my internal and I wanted to give KDE a try on my external. Also when I try to partition there's a lock next to my Ex HDD.

side question: what are the minimum requirements for KDE? I have P4 with 256MB RAM.

---

### Post by Steven_B on 2007-11-04
You can install and use Kubuntu without having to do a separate install:
[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

> Also when I try to partition there's a lock next to my Ex HDD.
That's probably because it's mounted.  Right-click on the partition and select "unmount".

If you still want to install Kubuntu on your external drive, plug it in, boot the Kubuntu Live CD, and install.  Just make sure that you select a partition on your external drive to be mounted as "/", and make sure you install the bootloader onto the external drive as well.  If you have doubts about how to do that, just ask or search around.
 
Your computer should be able to run KDE without any problems.

---

