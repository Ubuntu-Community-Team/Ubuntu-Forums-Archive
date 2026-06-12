---
title: "Not Enough Space"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by carrie.peary on 2006-10-29
I got to the partitioning part of install and it says that I don't have enough space, I've allocated 10GB to it and everything under that and still the error comes up. There is no other drives but one on my laptop and there are no other partitions. I defragmented yesterday and have a 80GB HD and am using 30GB of space.

Here is what it says for my "Manual partition" specs:

Partition  Filesys    Size    Used     Unused   Flags
/dev/hda1   ntfs    74.52GB  30.97GB  43.55GB    boot

thanks for any help.

---

### Post by PPAAUULL on 2006-10-29
Did you resize the NTFS partition? Is that where the problem comes up?

---

### Post by punx45 on 2006-10-29
check out this guide to partitioning with windows and ubuntu
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

also this install guide addresses partitioning too
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by carrie.peary on 2006-10-29
Yes, I do have a ton of white space at the end of my defragmentation...which is why this error is so strange. 

And i looked at those tutorials but I'm not all that handy with computers enough to want to manually try partitioning. I do understnad what it's suppose to do, but that's about it.

---

### Post by carrie.peary on 2006-10-29
I decided that I need to partition manually and here is my breakdown:

-80GB HDD
-Allot 60GB for Windows and 20GB for Ubuntu

-1GB swap
-9GB /
-10GB /home

my question is how to transfer that into the screens show here:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) (step 6)

---

