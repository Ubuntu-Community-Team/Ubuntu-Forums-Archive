---
title: "help me please"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by moondoggy17 on 2007-12-16
trying to install on friends cp but have never used the live cd install 
 i.m trying to partition but dont know what to set the "use as" setting to

---

### Post by jken146 on 2007-12-16
Try reading [www.psychocats.net/ubuntu/installing](www.psychocats.net/ubuntu/installing) to start with,  There are many other similar guides out there too.

As for partitioning, you need a partition for / and a swap partition (swap size = RAM x 2) as a minimum.  You may choose to have /home on a separate partition (I find it makes reinstalling totally painless).  So the labels in "Use as" are / and /home (swap has no label and you must use the filesystem type 'swap').

---

