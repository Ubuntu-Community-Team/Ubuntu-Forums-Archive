---
title: "Format Drive"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by psionman on 2007-03-24
I installed ubuntu using the desktop CD and manually partitioned by D: drive

I allowed the recommended space for swap & / and the remaining space was in a partition using fat32 filesystem

If I try to view D: in windows it says it is not formatted. Should I format it in Windows or will that wipe out ubuntu which is on the same physical disc?

Thanks

---

### Post by annda on 2007-03-24
you can safely format it under windows - it will affect just the partition, not the whole disk, and create a new logical drive with a new letter, like F: )

you can do it from within ubuntu, too, using mkdosfs (it's in the dosfstools available through the repositories).

if later you will want to use/mount the new partition, you will need to modify your /ect/fstab file. a good guide is here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by psionman on 2007-03-24
thanks annda

---

