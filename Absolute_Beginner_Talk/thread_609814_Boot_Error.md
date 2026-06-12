---
title: "Boot Error"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by arron on 2007-11-11
Hi.

I got a problem booting.  I have one drive hda with 4 partitions on it.  hda1 i use for playing with distros, installing a full distro on that partition only.  hda2 is my main os, fluxbuntu with my /home mounted to hda3.  These 3 partitions are ext3 format.  the last partition hda5 is my swap for what ever linux.

Anyhow, it is a amd64 machine.  Fluxbuntu is 32 bit only (for wine and stuff).  Yesterday I installed Ubuntu Studio 7.10 for amd64 to try it out on my hda1.

Now when I boot fluxbuntu i get the following error:

```
/dev/hda3: clean, 30261/9830400 files, 6289922/19653519 blocks
fsck.ext3: Unable to resolve 'UUID=76707fcc-7c32-414f-a65a-1281a825d71c'

fsck died with exit status 8
```

It goes to a prompt during boot.  If i hit control-d it will continue to boot, and work fine.  Ubuntu Studio does not seem to be affected.  I re-ran grub-install /dev/hda to see if it was a grub thing.  But that did not help.  I have done this before with other distros on hda1 (never amd64 though) and never had this happen.

How can i fix this?

Thanks.

---

### Post by taurus on 2007-11-11
You may want to change the UUID thing to the actual device name like /dev/hda3 in /etc/fstab and /boot/grub/menu.lst.

---

### Post by arron on 2007-11-11
Sweet, that did the trick.  Thanks!

---

