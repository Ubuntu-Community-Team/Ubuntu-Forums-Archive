---
title: "Lilo Help on upgrade"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by ronc55 on 2007-07-28
I am upgrading to ubuntu on a laptop setup for dual boot using Acronis.  The original Linux installation was Red Hat and I'm trying to use Lilo to install the desktop version of ubuntu.  I have copied the installation package after downloading it to a directory on the Red Hat partition.  The installation instructions found here:  [https://help.ubuntu.com/7.04/installation-guide/i386/ch05s01.html#boot-initrd](https://help.ubuntu.com/7.04/installation-guide/i386/ch05s01.html#boot-initrd) says I need to copy the following files "vmlinuz" and "initrd.gz from the Ubuntu archive.  Without these files nothing seems to happen.  Long winded question but I have spent the better part of two days trying to find these files.  Where are they?

---

### Post by DC@DR on 2007-07-28
You can find those 2 files on the root partition (of Ubuntu installtion) by going there:
```

$cd /
$ls -lah

```

---

