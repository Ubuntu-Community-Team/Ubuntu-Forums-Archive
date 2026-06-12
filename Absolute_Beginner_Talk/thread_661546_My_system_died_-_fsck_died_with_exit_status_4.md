---
title: "My system died - fsck died with exit status 4"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by niceguy123 on 2008-01-08
Is there any hope to get back to my Ubuntu desktop again? I am stuck on a black screen with code. that say: an automatic file system check (fsck) of the root filesystem failed. a manual fsck must be performed, then the system restarted

---

### Post by Raptor45 on 2008-01-08
Try starting the live CD, and using the terminal to scan the partition in question. "fsck /dev/sda#" where sda# is the partition.

---

### Post by ukripper on 2008-01-08
or you can use ```
sudo fsck -v /dev/sda
``` with verbose mode after booting into Live CD

where 'sda' is your current drive

---

### Post by xaxas on 2008-01-08
It happened to m,e and i just fixed this WITHOUT a Live CD :D
(I'm on Gutsy btw)

after the auto fsck fails it should let u type commands ...

type this : ```
fsck /dev/sda1
``` if ubuntu's on u're first partition :)

hope it helps :D

---

### Post by ukripper on 2008-01-09
I won't do fsck on the mounted partition you currently working on,  instead use live cd.

---

### Post by meindian523 on 2008-01-09
> **ukripper said:**
> I won't do fsck on the mounted partition you currently working on,  instead use live cd.

+1.

---

### Post by philinux on 2008-01-09
> **ukripper said:**
> I won't do fsck on the mounted partition you currently working on,  instead use live cd.

It's not mounted when the system drops out to the command line like this. And the system is being helpful telling you what to do.

a manual fsck must be performed

fsck -v /dev/sdxx will give you more info -v means verbose

---

### Post by meindian523 on 2008-01-09
You sure about that?
BTW,as insurance,you can try ```
umount -a
```

---

### Post by philinux on 2008-01-09
> **meindian523 said:**
> You sure about that?
BTW,as insurance,you can try ```
umount -a
```

In this instance positive. fsck would warn you anyway.

---

### Post by meindian523 on 2008-01-09
point,but is that a default that when fsck fails and drops to CLI and tells you to do a manual fsck,it has the target partition umounted?

---

### Post by philinux on 2008-01-09
> **meindian523 said:**
> point,but is that a default that when fsck fails and drops to CLI and tells you to do a manual fsck,it has the target partition umounted?

Yes because the file system has failed the check and hence not been mounted.

---

### Post by ukripper on 2008-01-09
> **philinux said:**
> Yes because the file system has failed the check and hence not been mounted.

interesting!

---

