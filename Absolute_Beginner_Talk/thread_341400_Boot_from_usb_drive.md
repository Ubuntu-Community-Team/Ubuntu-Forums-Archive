---
title: "Boot from usb drive"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by wehttamb on 2007-01-18
Hi

Is there any way i can boot off my usb drive if my bios does not allow it? I want it to boot puppy linux off my usb drive when i have it plugged in at startup. My main os is ubuntu though. Is there a bootable cd i can get which will boot off the usb drive?

Please help

Thanks

wehttamb

---

### Post by john_spiral on 2007-01-18
> **wehttamb said:**
> Hi

Is there any way i can boot off my usb drive if my bios does not allow it? I want it to boot puppy linux off my usb drive when i have it plugged in at startup. My main os is ubuntu though. Is there a bootable cd i can get which will boot off the usb drive?

Please help

Thanks

wehttamb

see the last item on the SLAX download page:

**SLAX Boot CD v 5.1.8**

[http://www.slax.org/download.php](http://www.slax.org/download.php)

looks like a way to boot from a USB key when your bios can't

---

### Post by wehttamb on 2007-01-18
I just tested it and it will only boot usb drives with slax. is there any cds that will boot all usb drives???

Thanks

---

### Post by john_spiral on 2007-01-20
ummmmmmmmmmm

I'm sure if we have a closer look at the slax cd we can make it boot another os on the usb drive.

mount the slax .iso and edit the file responsible for the kernel location. Might be as simple as editing the menu.lst file. Then reform the .iso file.

Linux format magazine had an excellent tut on this in dec 2005, **Build your own distro **

Anyone got any other suggestions?

---

### Post by wehttamb on 2007-01-21
i have no idea how to edit it. could u please tell me exactly what i have to do

---

### Post by john_spiral on 2007-01-24
looks like the below has all the info:

BootFromUSB

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by wehttamb on 2007-01-25
Yes, that looks like it has all the information but i dont understand what i have to do.

The reason i want to be able to use it off my usb drive is so i can boot off my usb drive at school and have a fully working linux (not a live cd) instead of using the windows xp which is on all of the computers.

Could you please tell me what i have to do to make this bootable cd.

Thanks

wehttaMB

---

### Post by john_spiral on 2007-01-28
Hi wehttamb,

Boot from the Ubuntu install CD, then choose your USB drive, normally sda1, as the destination drive for Ubuntu.

Then make a CD as described in the howto. This will allow you to boot from a USB drive, even if the computer's BIOS doesn't support USB booting.

Plug your USB drive into a computer and boot off the above CD, should boot you into Ubuntu off the USB drive.

Johne

---

