---
title: "Harddrive Question"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-25
I've got a portable harddrive attached to my computer via usb, and when I connect, the computer recognizes it and puts an icon on the desktop

the icon is named:
WD Passport

being the brand of the harddrive, my question is - is there a way to rename this icon? I'm not seeing anything when I right click on it.
This is probably a very basic question.

---

### Post by TidusBlade on 2007-12-25
Have you tried right clicking the Icon, properties and changing it there? You can also maybe change it using a partition manager like gparted for permanent changes.

---

### Post by LinuxIsInnovation on 2007-12-25
Try:
$ e2label device <labelname> -> for ext2 filesystem
or
$ mlabel device <labelname> -> for fat32 or fat16

---

### Post by forestpixie on 2007-12-25
I think this might help you

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

edit - which amounts to what sayakb says

---

