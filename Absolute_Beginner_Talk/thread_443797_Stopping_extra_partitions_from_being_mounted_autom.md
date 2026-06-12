---
title: "Stopping extra partitions from being mounted automatically"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-14
Hi,

I installed dual booted Edgy with XP on my computer recently and whenever I turn it on I get all the partitions on my hard drive showing up on my desktop including some weird partitions that were apparently there from the beginning like a 'DellUtility' and some other XP backup partition or something.  What I'd like to know is how to disable those two partitions from showing up at system start.

Thanks

---

### Post by taurus on 2007-05-14
Edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and put a # in front of those partitions, commenting them out.  Save the changes and reboot.

---

