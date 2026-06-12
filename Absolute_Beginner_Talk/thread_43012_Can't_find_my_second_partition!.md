---
title: "Can't find my second partition!"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by equal on 2005-06-20
Hi there, so I installed Ubuntu yesterday after 3 failed attempts at getting Win XP to install properly on my computer (service pack 2 issue). Anyways, I toyed around for a few hours, I finally got the hang of everything, but I have a question for you. 

While installing, I used the partition option to separate my harddrive into two separate sections, a 10GB primary, and a 50GB second partition. After installing Ubuntu, however, I was never able to figure out how to access the second partition. Eventually I just reformatted without partitioning and everything is running smoothly. I am still curious as to what I was doing wrong though. I would go into Places > Computer and into my local drive, and then I was lost. 

Thanks guys, glad to finally be here.

---

### Post by jdong on 2005-06-20
For Linux to "see" a partition as a filesystem (i.e. a directory structure), you must add a line in the /etc/fstab file, telling Linux about it.

---

### Post by poofyhairguy on 2005-06-20
Welcome.

You need to do this:

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by Ride Jib on 2005-06-20
also, when you made the second partition, if you specified it to be a certain directory (e.g. /home) it will not appear visually as another disk on the system, although it is actually there and in use...

---

