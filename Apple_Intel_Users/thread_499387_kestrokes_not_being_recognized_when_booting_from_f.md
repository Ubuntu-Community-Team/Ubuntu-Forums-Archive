---
title: "kestrokes not being recognized when booting from feisty installation cd"
date: 2007-07-12
forum: Apple Intel Users
---

### Post by oscar78 on 2007-07-12
I'm tyring to install Feisty on my new Macbook.  When booting from the installation cd,  the main ubuntu menu screen comes up but will not recognize any keystrokes....does anyone know whats going on?  Are there  separate installation cds for mac and windows users?  Perhaps I am using the wrong one.  

Thanks

---

### Post by cyberdork33 on 2007-07-12
known issue. happens in grub (bootloader) after ubuntu is installed as well. If you unplug and replug a USB keyboard on the selection screen it should start working (does for me anyway.)

---

### Post by blippy on 2007-07-14
> **cyberdork33 said:**
> known issue. happens in grub (bootloader) after ubuntu is installed as well. If you unplug and replug a USB keyboard on the selection screen it should start working (does for me anyway.)

Thanks for tip. I think the bug you are referring to is bug [36342]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/36342")

---

### Post by pxwpxw on 2007-07-14
I get this in starting the Desktop704 CD, i386 or amd64, on a Macbook c2d (about 3 times out of 4). Tried the USB keyboard trick, didn't work for me, well not that time anyway

Also been noted in rEFIt docs:

[http://refit.sourceforge.net/doc/c4s3_keyboard.html](http://refit.sourceforge.net/doc/c4s3_keyboard.html)
> 
General Keyboard Problems
Solution: This is a bug in Apple’s firmware. There is nothing rEFIt could do about this.

So far the only reports are from MacBook Pro Core 2 Duo models, but other Core 2 Duo models may be affected as well. Usually the keyboard works on some boots, but not every time. So the workaround is to reboot and try again.


---

