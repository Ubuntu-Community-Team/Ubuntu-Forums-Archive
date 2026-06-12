---
title: "Install Problem - No hard drive?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by AKCaveman on 2007-11-12
I burned the disk image to a cd and am running Ubuntu from it with ease but when i try to install it onto my hard drive in the select partition part of the installation nothing appears. I am running windows currently, is there something I need to change in my hard drive before it will be recognized by ubuntu?

I cannot move forward all it says is:

"No root file system is defined.

Please correct this from the partitioning menu."

But theres nothing to select?

---

### Post by taurus on 2007-11-12
Maybe these would help.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by AKCaveman on 2007-11-12
I'm still having the same problem. Is there a way to partition the drive so that I can run both windows and ubuntu? I only have one hard drive by the way which complicates things.

---

### Post by taurus on 2007-11-12
Use GParted LiveCD to resize your harddrive, [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/).  However, better back up your personal files first just in case.

Then, boot Ubuntu from a CD and tell the installer to install it on that newly empty partition.

---

