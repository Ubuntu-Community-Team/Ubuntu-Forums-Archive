---
title: "Can't see other hard drive"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by klife on 2007-11-04
I am a totally newbie. I installed ubuntu on a separate hard drive and have a boot grub. Why does windows not "see" my linux drive and vice versa.I am reading about wine but how can I run a windows program when I can't see those files?

---

### Post by Pumalite on 2007-11-04
sudo apt-get install ntfs-3g 
For Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/).
How did you install?

---

### Post by klife on 2007-11-04
I used a CD and it partitioned then set up grub.

---

### Post by klife on 2007-11-05
I get
ntfs-3g is already the newest version.
The following packages were automatically installed and are no longer required:
  apache2-utils libapr1 libarchive-zip-perl apache2 apache2.2-common libgsl0
  apache2-mpm-worker libfile-rsyncp-perl libaprutil1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

How do I use it?
Thanks for your patience it has been a difficult but rewarding expieriance installing ubuntu and upgrading until I reached gutsy

---

### Post by Pumalite on 2007-11-05
If Vista, you have to use Vista partitioner; otherwise Vista will not let you run anything in that computer.

---

### Post by klife on 2007-11-06
It is XP

---

### Post by Pumalite on 2007-11-06
The least of two evils. Good. You can install the driver I gave you in XP.

---

