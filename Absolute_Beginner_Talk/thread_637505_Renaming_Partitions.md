---
title: "Renaming Partitions"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-12-11
Even when I try to use gksudo I still can't rename the paritions on Hard Drives or USB Drives.

How do I do it?

---

### Post by FuturePilot on 2007-12-11
Have a look here
[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by laidback on 2007-12-11
This has worked for me when renaming the partitions on my 250Gb USB drive.

Changing /dev/sda5 to /media/usb_12_May_2007

In a terminal type:-
$mount (to get dev ids, in the example below I needed /dev/sda5)

then

$sudo e2label /dev/sda5 /media/usb_12_May_2007

In general  $sudo e2label oldname newname

$man e2label .....gives full details.

---

