---
title: "Plug and Play devices don't work?"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by charlybob on 2007-02-19
I don't mean in the main part of Ubuntu, I mean on the boot screen for the liveCD. I have to wait for the counter thing to get to 0 so that it automatically boots Ubuntu. I've tried setting the BIOS to manage plug and play stuff, but that didn't work either, I can only get the keyboard to do anything once it's started booting Ubuntu and finished the "setting up keyboard..." phase. 

I don't really want to try installing it now because of this because if I can't get past the dual boot screen, then my computers useless. I know I could just go get a PS/2 keyboard, but I don't actually need to use linux, it's more curiosity about what's different, so it doesn't matter that much, but does anyone know a way to get the keyboard to work before Ubuntu sets it up?

It's a USB Saitek one if it matters.

---

### Post by lhtown on 2007-02-19
It should work with a USB connection. You might make sure your keyboard is plugged into the back of your computer into the main usb ports and not in an add-on PCI card.

---

### Post by charlybob on 2007-02-22
I checked that, it was in a main USB port though, the mouse and wireless adaptor are taking the PCI ports.

Sorry for the kind of delayed reply, my internet's not been working too well lately.

---

### Post by netkid91 on 2007-02-22
Check out the BIOS screen, look through ALL the screens, but only touch something similar to "USB Keyboard Support".  Might be a little difficult without a PS/2 one though.....just see if you can get into the BIOS for now.

---

### Post by charlybob on 2007-02-23
Yeah I've checked in the BIOS before. Most relevant thing I could find was BIOS management of PNP devices. Turned it to yes, but it didn't work.

---

### Post by netkid91 on 2007-02-23
Well, PNP devices has nothing to do with protected mode USB keyboard support.  It seems that your MoBo doesn't support USB keyboards at boot time, so the only way you can fix the problem is with a PS/2 keyboard, sorry about that.
If there is anything else that you need, just ask.

---

