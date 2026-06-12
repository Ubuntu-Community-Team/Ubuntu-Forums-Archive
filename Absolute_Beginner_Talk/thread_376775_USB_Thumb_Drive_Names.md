---
title: "USB Thumb Drive Names"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by drs305 on 2007-03-05
I have 3 usb thumb drives. I have removed all references to them in fstab. Two automount as /dev/sda1 and the third mounts as /dev/sda . I would like them all to consistently be recognized as /dev/sda1.  I am not referring to the mount point, which I know I can control; I don't know how or where the sda vs sda1 reference is stored. I think somewhere I read that this type of thing is written when the drive is recognized for the first time. 

How can I change the reference to the third thumb drive to sda1, if that is possible?

Thanks.

---

### Post by drs305 on 2007-03-05
I believe I've answered my own question. I found that the number following "sda" is associated with a partition number (ie sda1 is partition 1 of sda). I reformatted the usb drive listed as sda by using gparted (sudo gparted) and as soon as I did so it created partition 1 and now shows up as sda1 (/dev/sda1). I didn't realize that there could be data on a thumb drive without a partition, but apparently that is what happened since I could read lots of data on the drive when it was listed as sda.

---

