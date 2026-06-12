---
title: "Screw up on somthing"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by dthreap on 2006-09-22
Well I just installed ubuntu lastnight(version 5.10 and updated it) and I think when I made a partition for it somehow I delete windows... Here is the picture of the windows partition

[img]http://www.upit.be/uploads/images/screenshot38514.png[/img]

Is there anything I can do? Because There were a few things I really needed on there.

Thanks

---

### Post by podunk on 2006-09-22
I'm very new to Linux my self - so take that into consideration.

As I understand it though Linux names your first hard drive
hda
and the partions on that drive are numbered
hda1
hda2
and so on.

My computer has 2 hard drives with several partitions each. The first hard drive has Windows and it divided like this
hda1
hda2
hda3
hda4

The other hard drive is 
hdb1
hdb2
hdb3

do you have 3 hard drives on your computer? hdc for me is a USB flash drive - so maybe you're OK?

try this, type

sudo fdisk -l 
(that is a lower case L at the end not an I)
enter your password and see if hda and hdb are there.

Hope you didn't format your drive! The back up tools that come with Windows really suck, there is a freeware program called Renaissance that works pretty good.

---

