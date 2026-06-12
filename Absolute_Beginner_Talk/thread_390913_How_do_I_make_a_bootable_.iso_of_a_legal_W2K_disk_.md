---
title: "How do I make a bootable .iso of a legal W2K disk for use with VMware"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by frankelr on 2007-03-22
What available Ubuntu program do I use to create a bootable
image of a W2K install disk.  My intention is to use VMware to turn the image 
into a W2K virtual OS with Ubuntu as a host.  The forums mention mkisofs,
isomaster Any suggestions gratefully received

---

### Post by Scunizi on 2007-03-22
Pop the CD in the drive and wait for the icon to show up on the desktop.  Then right mouse click and choose copy.  A new box will appear.  Change the destination drive to file and hit go.  That should do it.

---

### Post by Bachstelze on 2007-03-22
In a terminal :

```
dd if=/dev/hdc of=image.iso
```

of course, remember to change /dev/hdc to the path of your CDROM drive if it's diffrent.

---

### Post by frankelr on 2007-03-22
Thank You both for your help,

Bob

---

