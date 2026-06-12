---
title: "usb hard disk"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Mick8882003 on 2008-03-27
I am having trouble with a usb hard disk, it has the same name a folder in my root? folder on my pc, what is the easyiest way to format this so i can use the usb hard disk again???

---

### Post by codeslicer on 2008-03-27
Open up a nautilus file browser and go to computer. You don't see it there?

---

### Post by stefangr1 on 2008-03-27
You could look up the device name with:

fdisk -l

and then partition it with:

gparted /dev/###

---

### Post by Mick8882003 on 2008-03-27
No i dont, I am thinking i will have to format it atm, its windoz and i would like to get it up and running.

---

### Post by Mick8882003 on 2008-03-27
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9ea6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29647   238139496   83  Linux
/dev/sda2           29648       30401     6056505    5  Extended
/dev/sda5           29648       30401     6056473+  82  Linux swap / Solaris


thats all i get

---

### Post by codeslicer on 2008-03-27
And it's not the first 250GB one?

---

### Post by Mick8882003 on 2008-03-27
noo, its a 100gig one (usb)

---

### Post by stefangr1 on 2008-03-27
The 250GB one is obviously the normal system hdd. You could try to run fdisk -l as root user, to see if it shows up then (maybe you already did?), but I think your drive is just not recognized at all somehow.

---

### Post by Mick8882003 on 2008-03-27
ill format it with my lappy, is there ne way of formatting it and still keep it readable by windoz?

---

### Post by stefangr1 on 2008-03-27
Yes, then you should format it as FAT32, so you can access it from both windows and linux. Disadvantage of that is that you can't store files over 4GB, like hd-movies or dvd images on it.

---

