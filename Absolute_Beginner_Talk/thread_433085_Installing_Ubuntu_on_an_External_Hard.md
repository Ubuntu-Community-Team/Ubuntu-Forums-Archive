---
title: "Installing Ubuntu on an External Hard"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by milad on 2007-05-04
I have an external hard drive for my laptop which is connected to my PC using a USB cable. Is it possible to install Ubuntu on this drive?
I am not sure but I think it's not possible to boot up a computer from a USB device but i have a friend who keeps on telling me that i'm wrong.

---

### Post by logos34 on 2007-05-04
> I am not sure but I think it's not possible to boot up a computer from a USB device

some can, some can't...check your BIOS.

---

### Post by milad on 2007-05-04
Well, assume that my BIOS supports them. Does it mean that I can install Ubuntu on my USB Hard drive? That would be so cool

---

### Post by starcraft.man on 2007-05-04
Yup, long as your BIOS has the ability to boot a USB drive then your set. Just boot into the live or alternate CD and make sure when you partition your doing it on your USB drive, then, your GRUB will install on the computers MBR and you should be able to boot into the USB with no problems :)

Have fun being a cool geek with a portable Ubuntu :D

---

### Post by logos34 on 2007-05-04
Then you *should* be able to...I'd use the ubuntu Alternate CD, which allows you to specify where GRUB bootloader gets installed...You want it on the MBR of the usb drive, not the internal.

---

### Post by milad on 2007-05-04
TX guys. I'm gonna give it a try

---

