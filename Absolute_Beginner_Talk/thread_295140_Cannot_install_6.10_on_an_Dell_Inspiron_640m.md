---
title: "Cannot install 6.10 on an Dell Inspiron 640m"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Razorhack on 2006-11-07
I have just purchased an Dell Inspiron 640M and tried the 6.10 LiveCD. It wouldn't boot at all. First it wouldn't start xserver because this laptop uses the 915 chipset. I expected this from other posts on this forum. But after the xserver fail message I got no further than fck -->(ok) message.  The cursor is blinking but nothing happens.  I waited for an hour and nothing more happened.  I scanned the CD for defects and it found none. 

I found this but it really don't fix my problem. [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron640m]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron640m")

 

I see from other posts that people have had trouble with the installation and any help would be deeply appreciated. Please remember that I am a complete neophyte to Linux/Ubuntu :)

---

### Post by sandeep.rajarao on 2006-11-21
Had the same problem.  Just connected a LCD monitor port (which supports only 1024x768).  While installed used F4 to select 1024x768 and also used F6 to set boot options.  Added vga=771 and tried installing.  It worked.

After booting now I am trying to install 915 resolution.

Edgy eft detects and brings up 2 CPUs which was not the case with Dapper.

Sandeep

---

### Post by tschneiter on 2007-02-01
I couldnt install 6.10 directly (640m here as well). I tried hooking up an external monitor, I tried safe mode, I tried vga=771, no dice. Soooo my solution was to install dapper in safe mode, then upgrade to edgy, which worked wonderfully. Dont know if I missed out on anything by doing the upgrade rather than a fresh install, but everything seems to work alright, except acpi.

---

### Post by m_janos on 2007-02-10
I had no problem installing the software. I do have an external LCD attached to my machine but it quite happily booted on the Laptop screen. I haven't tried it while disconnected from the external display but the way my xorg.conf looks, I feel that it treats the external monitor as the main display and the internal monitor as a secondary display.

Michael

---

