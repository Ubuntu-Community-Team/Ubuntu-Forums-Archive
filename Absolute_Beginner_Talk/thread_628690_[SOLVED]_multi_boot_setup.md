---
title: "[SOLVED] multi boot setup"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by k2can on 2007-12-01
I have Win2000Pro installed on one partition. I just installed Ubuntu Desktp 7.10 on the same drive.
How do I setup the system to allow multi boot ?

---

### Post by teryowen on 2007-12-01
boot into ubuntu if you can rite now, if not boot off a live CD.

and type this in terminal:

sudo fdisk -l

copy and paste the output.

---

### Post by overdrank on 2007-12-01
> **k2can said:**
> I have Win2000Pro installed on one partition. I just installed Ubuntu Desktp 7.10 on the same drive.
How do I setup the system to allow multi boot ?

Hi and welcome, if you installed Ubuntu correctly then you should have grub installed and be able to boot to windows or Ubuntu.  
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by k2can on 2007-12-01
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24429d67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

---

### Post by overdrank on 2007-12-01
> **k2can said:**
> Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24429d67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Hi and it looks like you install Ubuntu over the windows partition. :(

---

### Post by k2can on 2007-12-01
Thanks.. not what I wanted to hear but no big deal. I will reload Windoz and start over.

---

