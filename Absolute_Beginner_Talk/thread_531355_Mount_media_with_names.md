---
title: "Mount media with names"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by skyttan on 2007-08-21
Hello!

There's one think I really hate about Linux - mounting volumes. At most I hate accessing my external HDD as 'disk' and then I plug in my other HDD who gets the name 'disk-1' :@ ... In Windows you could name them to like "Peter's 320GB".
   Only because of this I formatted my bigger HDD to NTFS and plugged it in to a Windows computer. There I named it and now it pop-ups with that name in Windows. 

My question is: How can I mount my external HDD with file system ext3 with a name I like?

Thankful for answers,
skyttan

---

### Post by kinematic on 2007-08-21
sudo e2label /dev/whatever nameyouwant

edit:you have to reboot for it to take affect.

---

### Post by skyttan on 2007-08-22
Thanks! :D

Is it permanent?

EDIT: With your command 'sudo e2label /dev/whatever nameyouwant' - wich hard-drive am I swithing name on? How do I know?

---

### Post by vanadium on 2007-08-22
See here

[http://www.debuntu.org/device-partition-labeling](http://www.debuntu.org/device-partition-labeling)

---

### Post by kinematic on 2007-08-22
use the command ```
sudo fdisk -l
``` with the external plugged in to see what the device name is. And yes, it is permanent until you change it.

---

### Post by mikex on 2007-08-22
I was playing with naming last night,and I noticed Nautilus had a menu where you could type in a new name for a device, but the name wouldn't be accepted, even when you do a gksudo nautilus. What is this naming dialog box for in nautilus?

---

### Post by skyttan on 2007-08-24
Thanks a lot!

It really work! :D Easy-peasy man... Hope this will be standard and with a GUI so everyone can do this in the future without any problem.

Thanks again!
skyttan

---

