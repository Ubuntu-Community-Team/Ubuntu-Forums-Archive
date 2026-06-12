---
title: "help using FSCK"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2007-12-15
how do I run it? Someone told me that I need to verify my filesystem integrity. is it a grub command line  ?

---

### Post by ac7ss on 2007-12-15
Simply put, you type ```
sudo fsck /dev/hda1
``` at a prompt with /dev/hda1 replaced with the proper device file for the drive. HOWEVER! please read the man page ```
man fsck
``` as you should with any command that you use with sudo.

Sometimes the repairs must be done with the drive unmounted. You can do this from a live CD or the system may automatically drop you to a root shell with all drives unmounted after finding a particular error.

---

