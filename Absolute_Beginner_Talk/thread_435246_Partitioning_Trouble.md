---
title: "Partitioning Trouble"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by cygnis1 on 2007-05-06
Yesterday I tried to install Ubuntu 7.10.  I was at the partitioning section and was choosing a size for the swap partition.  I found out too/. late that I mistakenly made the partition too small.  I canceled the installation (stupid,I know).  Now when I try to install Ubuntu, choose manual, it shows /dev/sda. There are four  partitions /dev/sda1dev/sda2, /dev/sda5, and /dev/sda6.  Total space is 250055MB.  What do I do?  I am afraid I have screwed up my hard drive.  Is there any other way to install Ubuntu?  Can I fix my hardrive partitions?
Thanks,
Cygnis 1

---

### Post by Happy_Man on 2007-05-06
From the LiveCD, go into System --> Administration --> GNOME Partition Editor. And then retweak your partitions to your hearts content. And then reinstall, and make sure not to kill it in the middle. :razz:

---

### Post by cypherzero on 2007-05-06
Yes, you can always change your partitions later. Ubuntu has lots of nice tools for that.
There's nothing wrong with killing the install either, you can reinstall later.

---

### Post by cygnis1 on 2007-05-06
Retweaking how?  I do not know how to retweak it  to the same as before.
Thanks
cygnis1

---

### Post by mikewhatever on 2007-05-06
:)

---

### Post by mikewhatever on 2007-05-06
Why don't you start from specifying what or how it was before. Have you had Windows or another OS installed? Does it still work?

---

### Post by cygnis1 on 2007-05-06
When I first got to the partitioning portion of the install, it showed all the partitions in the hd. 250 MBgig hd  /dev/sda1ntfs 64gig, /dev/sda2 fat32, /dev/sda5 ntfs 107gig, /dev/sda6 ntfs 52gig.  This is what shows up in Gparted while in ubuntu live cd.  When trying to install ubuntu manually handling the partition its shows /dev/sda1 ntfs  /media/sda1  69051 MB, /dev/sda2 FAT32 /media/sda2  9121MB, /dev/sda5 ntfs /media/sda5 115359MB, /dev/sda6 ntfs /media/sda6MB.

---

### Post by mikewhatever on 2007-05-08
Well. you seem to have the same four partitions as before, so no new ones had been created. Here is some documentation on how to use gparted, Ubuntu partitioning tool.
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

