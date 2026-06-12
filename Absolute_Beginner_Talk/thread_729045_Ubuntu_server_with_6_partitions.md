---
title: "Ubuntu server with 6 partitions"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by medha on 2008-03-19
Hi Everyone!

I am trying to install Ubuntu server and I need about 6 partitions, each for  a VM. Ubuntu doesnt let me do more than 4 partitions. Is there a way around this?

---

### Post by Scorpuk on 2008-03-19
Not 100% sure on this, but...


If you are going to join the partitions together under LVM then can't you add more partitions at a later date.

ie. install with what partitions you can create and then use parted / gparted to create the other partitions and then add them to the LVM.

---

### Post by Golem XIV on 2008-03-19
You can have up to 4 **primary** partitions.  Just create a secondary partition and inside it create the other ones as logical partitions.

Note:  this may be Windowspeak, I don't know if Linux uses the same terminology... :)

---

### Post by medha on 2008-03-19
Thanks people! 

This also has more information:
[http://ubuntuforums.org/showthread.php?t=251873](http://ubuntuforums.org/showthread.php?t=251873)

---

### Post by Ptero-4 on 2008-03-19
You can't create more than 4 primary partitions. But you can create 3 primary and one extended with the other 3 as logical partitions.

---

