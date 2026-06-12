---
title: "usb keyboards not working in grub menu"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-06-11
Can someone tell me why my 2 usb keyboards do not work on the grub menu, unless a ps/2 keyboard is plugged in, and then both keyboards work. This is very annoying having to have another keyboard plugged in, And it would be appreciated if I can have any answers, I mean, this must be a common problem right?

[Also, this happened on my old pc as well.]

---

### Post by Songwind on 2007-06-11
does your BIOS have a "USB Keyboard support" option?  Is it turned on?

---

### Post by Terl on 2007-06-11
I had this happen to one of my pc's.  I found a setting in bios to turn usb on at boot.  Might be worth checking your bios.

---

### Post by moredhel on 2007-06-11
Fixed, I thought usb support was enabled, and it was. It turns out there were two things though:

usb keyboard support
enhanced usb keyboard

The 2nd one sounded dodgy, so i disabled it and it worked.

:D

---

### Post by Red David on 2007-06-19
Definitely a common problem. I'm a complete newbie and was rather dismayed to discover that I couldn't choose to boot xp on my (former master) slave drive because I couldn't arrow down in the grub menu and pick xp. I'd begun to suspect it had something to do with the keyboard (my really nice $1 yard sale Macally) so I spent $2 for a ps2 key board today and all is well. Guess I'll have to check the bios next.

---

