---
title: "read/write permisions"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-27
how can i set write permissions to a volume- for example to create files and folders?  i just created 2 new ext3 partitions on a second hard drives, and i noticed that when i go into these volumes i cannot create anything.  i would like to be able to do this through nautilus if possible.  thanks.

---

### Post by taurus on 2008-01-27
You can either run nautilus with root privilege

```
gksudo nautilus
```
or you can change the owner of that new mount point of your second harddrive from root to your login name so you can write to it anytime you want.

---

### Post by Matt26 on 2008-01-27
how do i change the owner of the mount point?

---

### Post by Alberio on 2008-01-27
If i'm not mistaken, the owner will be root. chown will not work for these, it won't work if you chown /dev/s(a,b,c,)(1,2,3) either

what you can do, though, is use the umask option in fstab. There should be an fstab tutorial around here somewhere. 

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

those are where I learned

---

