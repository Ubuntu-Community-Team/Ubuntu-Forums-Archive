---
title: "HelP! using LiveCd how to mount an HFS drive as read write?"
date: 2008-01-26
forum: Apple Intel Users
---

### Post by ironslave on 2008-01-26
i am trying to Edit some files in live Cd mode to get my mac back but when i mount the Drive in liveCd it comes up as read only!
here is how i mounted the drive

sudo su -
modprobe hfs
modprobe ufs
modprobe hfsplus
mkdir ~/Mac
mount -t hfsplus /dev/sda1 ~/Mac

SUDO nautilus opens in root mode but the drive is still read only

---

### Post by cyberdork33 on 2008-01-26
> **ironslave said:**
> i am trying to Edit some files in live Cd mode to get my mac back but when i mount the Drive in liveCd it comes up as read only!
here is how i mounted the drive

sudo su -
modprobe hfs
modprobe ufs
modprobe hfsplus
mkdir ~/Mac
mount -t hfsplus /dev/sda1 ~/Mac

SUDO nautilus opens in root mode but the drive is still read onlyIs journaling disabled?

try editing/creating a file with nano to make sure it is not just an issue with nautilus.

---

