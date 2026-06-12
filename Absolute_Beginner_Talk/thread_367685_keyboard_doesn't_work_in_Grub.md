---
title: "keyboard doesn't work in Grub"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by wood144 on 2007-02-22
I am attempting a dual boot system with Unbutu and Windows XP pro, i got ubuntu to install and the grub menu comes up when i reboot, but none of the keys on my keyboard work until i'm already inside of an OS so i can't change from the default selection.  I am using a Saitek Eclipse II thgough a USB 1.1 port. any ideas?

---

### Post by mcduck on 2007-02-22
Sound like you need to enable legacy support for keyboard & mouse in your computer's BIOS..

edit: I just realized that it might be a bit hard thing to do if your keyboard doesn't work.. You'll need to borrow a keyboard with PS/2 connector from somebody to do it.

---

### Post by igknighted on 2007-02-22
> **mcduck said:**
> Sound like you need to enable legacy support for keyboard & mouse in your computer's BIOS..

I don't know if it is so much legacy support as USB input device support.  If your BIOS does not have such an option, consider spending a few bucks to get a ps/2 adaptor.

---

### Post by Sunflower1970 on 2007-02-22
I had this trouble with my old Compaq. Couldn't use the USB keyboard in GRUB, although it worked fine once booted in to 98 (the original install) and now Ubuntu. I tried switching the BIOS for legacy support, and that didn't work. I also tried an adapter. I tried one I had laying around the house, normally used for a mouse, and when that didn't work I bought one for like $2 that was specific to a keyboard, and it didn't work either. The adapter is kind of an iffy thing. For some people it works, others it dioesn't. 

In the end, I got a new non-USB keyboard. Now it works great :)

---

### Post by wood144 on 2007-02-22
thanks for all the replies.

I have procured a USB to PS/2 adapter that was laying around my place of employment, and i'll look into the BIOS settings.  Worse comes to worse i think i have an old PS/2 keyboard in a closet somewhere.

---

### Post by SilverWave on 2007-07-29
Hidden BIOS setting:
Pheonix Awardbios > integrated peripherals > on-chip PCI device > USB keyboard support vis > set this to BIOS from the OS default.

---

