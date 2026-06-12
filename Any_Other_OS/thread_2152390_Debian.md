---
title: "Debian"
date: 2013-06-07
forum: Any Other OS
---

### Post by yakult on 2013-06-07
The key for install is DEV/**???
Sure the file is CD-ROM ISO and the install not running!!!
Left one user?

---

### Post by vadimkolchev on 2013-06-07
Not sure I understand what your problem exactly is. Could you be more specific please? I had no problem with debian install when I tried it last week.

---

### Post by BBQdave on 2013-06-08
> **yakult said:**
> The key for install...

Just a guess, but may be helpful... [http://ubuntuforums.org/showthread.php?t=2147015](http://ubuntuforums.org/showthread.php?t=2147015)

[Debian 7 non-free firmware]("http://www.debian.org/releases/stable/debian-installer/")

Check out the message box:

:arrow: If any of the hardware in your system **requires non-free firmware to be loaded** with the device driver...

I downloaded the tarballs of common firmware packages and unpacked them  onto a USB stick. Plug in the USB stick - non free firmware packages,  and boot up Debian 7 Net-Install CD. Going through the install process,  Debian 7 installer will access the USB stick for the missing non free  firmware - needed for your hardware.

Was able to easily *wireless* net install Debian 7 on my Toshiba Satellite C655 notebook :smile:

---

