---
title: "The Partition is not Working"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-09-08
Hey guys. Well, I got to the partitioning point in the installation process, when I got this error:

> An error occurred while writing the changes to the storage devices.

The resize operation is aborted.

Does anyone know why I get this message and how I can fix it? Thanks.

---

### Post by bodhi.zazen on 2007-09-08
Hard to know for sure, I would advise two things :

1. Did you defragment first ? Sometimes fragmentation causes problems when trying to resize.

2. The other problem I have seen is that  you can not re-size a partition if it is mounted. Sometimes the partition automounts :

Go to System > Preferences > Removable Drives and Media and uncheck the box about automatically mounting drives.

---

### Post by drndrw on 2007-09-08
Ah, okay. Well I just tried creating a few new partitions in Gparted, so I'll see how that works. And how do I defragment a hard drive?

---

### Post by bodhi.zazen on 2007-09-08
Boot to windows 

Menu -> All Programs -> Accessories -> System tools -> disk defragmenter

---

### Post by drndrw on 2007-09-08
I am currently running Xubuntu though... Can I still do this on this OS?

---

### Post by bodhi.zazen on 2007-09-08
Do what ? You need to defragment from windows

---

### Post by drndrw on 2007-09-11
Somehow, I fixed the error. But thanks :)!

---

