---
title: "scsi device names wrong during install on old Mac"
date: 2005-10-11
forum: Apple PPC Users
---

### Post by tonyB on 2005-10-11
The first time I tried to install ubuntu linux (warty) I had a problem with the scsi device names not being correct.  For example, the disk I wanted to install on would normally (using a different linux dist) be /dev/sdb, but when I got to the partitioning during install the device would show up as /dev/sda or /dev/sdc (I've forgotten which).  The order of all three disks was different from the normal, correct order.  I finally realized I had not done a modprobe mesh after booting the install cd, and when I did that the order was correct.  Install went fine, and I've been *delighted* with this distribution ever since.  Hoary install went fine.

I tried to install breezy a while ago, and the order is, once again, incorrect even though I have done the modprobe mesh.  The only difference I can think of is that I have an external usb disk now.  Anyone else see anything like this?  Any suggestions?

My system: Mac 7300 w/G3 upgrade card. Warty and Hoary on external scsi drives.  Mac OS on internal drive.

Thanks in advance,
tony

---

