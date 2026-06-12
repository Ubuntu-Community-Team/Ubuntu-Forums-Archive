---
title: "deleting pics from a camera"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-22
I just picked up a Canon A460. Works great for importing photos. I have another mem card with like 200pics on it. I want to be able to delete them from the comp, but the camera does not show up as a disk drive, and am unsure how to do anything but import with f-spot. 

suggestions?

edit: when I say delete from comp, I mean delete them from the mem card as it is connected to the computer through the camera, so I do not have to delete one by one via camera controls.

---

### Post by raul_ on 2007-06-22
could you post the output of

fdisk -l

with the camera plugged in?

---

### Post by FleetAdmiral74 on 2007-06-23
ed@database:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9964    80035798+  83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1216     9767488+  83  Linux
/dev/hdb2            1217        1338      979965   82  Linux swap / Solaris
/dev/hdb3            1339       13496    97659135    5  Extended
/dev/hdb5            1339       13496    97659103+  83  Linux
ed@database:~$

---

### Post by FleetAdmiral74 on 2007-06-23
bumpity bump

---

### Post by fdrake on 2007-06-23
> **FleetAdmiral74 said:**
> 

edit: when I say delete from comp, I mean delete them from the mem card as it is connected to the computer through the camera, so I do not have to delete one by one via camera controls.

don't u have an option "SELECT ALL"?

---

### Post by Swab on 2007-06-23
Doesn't the camera have an option to format the card?

---

### Post by oilchangeguy on 2007-06-23
> **Swab said:**
> Doesn't the camera have an option to format the card?

you probably don't want to format the card. but you can't tell me there's not an option to delete everything on the card, not just one at a time. try pushing the cameras menu button, and read the options. or read the owners manual for the camera.

---

