---
title: "cant get usb drives to work!?!"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2007-04-30
im using feisty and i plug in usb drives but they dont automount and i dont know how to find em. but when i plug in my camera it automounts and asks me to import. wtf?

:confused:

---

### Post by mikeyphi on 2007-04-30
Have a look under System - Preferences - Removable Drives and Media......make sure the boxes are ticked.

If no action after that.look under Places - Computer 
If it is shown - right click and Mount.

If still no action
Open a terminal and type:

sudo mount -t vfat /dev/sda1 /mnt

assuming you don't have any SATA drives...otherwise instead of sda1 use the next avalable sd** number.
you have to look in the /mnt directory to find your files
remember to unmount before removing:

unmount /dev/sda1

---

