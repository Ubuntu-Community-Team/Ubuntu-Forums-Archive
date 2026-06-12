---
title: "ejecting flash drive"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-01-14
why I can't eject my usb flash drive? the option isn't appearing any more!
It is a Kingston 2GB data traveler

---

### Post by Sef on 2007-01-14
When you right click, there is no option for eject?

---

### Post by Megabuntu on 2007-01-17
I have a sandisk cruzer micro that when I right click the icon on the desktop I don't have an eject option.:frown:

---

### Post by Pobega on 2007-01-17
All you have to do is unmount it, to unmount you can either use> user@comp~:$ umount /dev/*or you can right click the icon on your desktop and simply click "Unmount". Ejecting isn't nessecary in Ubuntu :)

---

### Post by Megabuntu on 2007-01-17
Does it not matter that the icon remains on the desktop even when I "unmount volume"?

---

### Post by peter_brewer on 2007-01-17
I have noticed this to.  On volumes over a gig the eject option doesn't appear on the desktop.  However if you go to the system menu and then media devices you should be able to eject from in there or alternatively go to konqueror and then /media and right click and remove device there.

---

### Post by Pobega on 2007-01-17
> **peter_brewer said:**
> I have noticed this to.  On volumes over a gig the eject option doesn't appear on the desktop.  However if you go to the system menu and then media devices you should be able to eject from in there or alternatively go to konqueror and then /media and right click and remove device there.

As far as I know only iPods and CDs need ejecting, I have both a 4 GB flash card and a 64 MB flash card and neither of them have an eject option.

> Does it not matter that the icon remains on the desktop even when I "unmount volume"?

Nope, doesn't matter. It's on the desktop because your computer knows it's connected, not mounted. Basically, all mounting does is give you the ability to read from and write to the device; Having a device plugged in and unmounted gives you the ability to partition it. So you can benefit from both, theoretically.

---

