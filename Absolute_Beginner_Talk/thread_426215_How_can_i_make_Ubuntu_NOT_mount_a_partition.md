---
title: "How can i make Ubuntu NOT mount a partition?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-04-28
I have a Dell MediaDirect partition that FF cannot read, and every time it tries, it does something with the lead clusters that MediaDirect must then fix every time it is booted.  Is there a way to tell FF to not mount it every time it boots?

---

### Post by vanadium on 2007-04-28
You probably will need to remove the entry for that partition in /etc/fstab. To my knowledge, only partitions that are listed in /etc/fstab are mounted at boot time. 

An item can be removed by either deleting the entire line. A safer approach is to "comment it out", i.e., add a # at the start of the line.

To edit the file:

gksudo gedit /etc/fstab

---

