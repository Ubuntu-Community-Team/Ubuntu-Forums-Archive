---
title: "Mounting root file system fails ?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by TheOther on 2007-02-25
After a week of operating my ubuntu system (6.06) stopt on mounting root file system. 

The screen shows (character mode) a lot of text. Errors reported in this screen are:
mount: Mounting /dev/hdf1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

Then BusyBox is started and gives the error:
/bin/sh : can't access tty; job control turned off

What can I do to correct whatever is going on.
Please help.

---

### Post by Koybe on 2007-02-25
When you get to the grub menu... what choices do you have? It should be a misconfigured option.

---

### Post by TheOther on 2007-02-25
> **Koybe said:**
> When you get to the grub menu... what choices do you have? It should be a misconfigured option.

I have the options:
Ubuntu 2.6.15-28-386
Ubuntu 2.6.15-28-386 (recovery mode)
Ubuntu 2.6.15-23-386
Ubuntu 2.6.15-23-386 (recovery mode)
memtest86+

(and an option for XP; XP is running fine on the first hard disk. The second hard disk is Ubuntu and is visible in XP (computer management) with two partitions.) 

All the Ubuntu options result in the same errors. Where do I start trouble shooting?

---

### Post by TheOther on 2007-02-25
Sorry!
I did miss something. I boot the system again and there were two more errors:

[17179676.944000] EXT3-fs error (device hdf1): ext_check_descriptors: Inode bitmap for group 448 not in group (block 2147483647)!
[17179676.948000] EXT3-fs: group descriptors corrupted!

Then the mounting errors appear.

Can this be corrected? How?

---

### Post by Koybe on 2007-02-26
You should try booting a live cd and repair your FS with fsck.ext3 or something like this.

---

### Post by TheOther on 2007-02-26
Thank you, Koybe. 

For the absolute beginners (like me) I burned a Ubuntu desktop CD. Started it and in the ' terminal' I entered the command:

Sudo fsck.ext3 /dev/hdf1 

I did give serveral 'Y'es on the questions to fix the errors. And the result is a working system.

---

### Post by bodhi.zazen on 2007-02-26
FYI

```
fsck -rfv /dev/hdxy
```

where hdxy is your partition to fix is even easier :)

see man fsck for further information.

---

