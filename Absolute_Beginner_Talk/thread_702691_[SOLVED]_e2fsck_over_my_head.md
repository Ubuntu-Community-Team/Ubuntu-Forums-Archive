---
title: "[SOLVED] e2fsck over my head"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-20
Just purchased a new hard drive 750gb
seems fine 
formated the drive to ext3
on startup i get some thing like this
```
joe@joe:~$ sudo e2fsck /dev/sda
[sudo] password for joe:
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

so what that mean

i figured that its just what ever so i reformated and then it dose the same thing

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-20
hahaha
think i fixed it
need to add a 1 at the end of /dev/sda in /etc/fstab

---

### Post by ahsile on 2008-02-20
Yep, you got it.

/dev/sda is the drive
/dev/sda1 is your ext3 partition

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-20
haha just rebooted its fixed

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-20
> **ahsile said:**
> Yep, you got it.

/dev/sda is the drive
/dev/sda1 is your ext3 partition

ya i know i couldn't figure out why it was checking the entire drive

---

### Post by jan quark on 2008-02-20
please mark solve threads as solved to help other users to find the their solution faster
thank you

edit :

you were faster than I 
sorry

---

