---
title: "Grb error 5 after adding  a new HD"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by gene74 on 2007-08-16
I bought a new HD ( SATA ) and when i powered back the PC, i get error 5. I had to disconnect the new HD so i can boot up to either XP or ubuntu. What do i need to do so ?

---

### Post by Jimmyfj on 2007-08-16
Did you check the device sequence in your computers BIOS ? Is this set to boot SATA before PATA? 

I run both IDE and SATA on my computer, and have no issues with that, I just told my BIOS to look for SATA before IDE

---

### Post by jtraub on 2007-08-16
This means, that your partition table is corrupted.

---

### Post by Jimmyfj on 2007-08-16
> **jtraub said:**
> This means, that your partition table is corrupted.

This is NOT correct - This does not explain that when disconnecting the SATA drive the computer boots up fine - Just make sure that your first boot device is Cd-ROM then IDE and make sure that your SATA disk is not set as a boot device. This should do the trick.

More info here:  [http://www.linuxquestions.org/questions/showthread.php?t=576237](http://www.linuxquestions.org/questions/showthread.php?t=576237)

---

### Post by gene74 on 2007-08-16
Thank you guys, will try this tonite.

---

### Post by vexorian on 2007-08-16
Well only explanation is that it is connected as master when you wanted slave? Well, something like that, connecting the hard drive is probably changing the hd order, so when grub tries to boot hd0,1 it finds the new empty hard drive.

Try using a live cd to restore grub

---

