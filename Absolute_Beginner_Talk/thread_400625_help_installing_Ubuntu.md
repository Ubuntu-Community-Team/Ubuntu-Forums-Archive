---
title: "help installing Ubuntu"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by ssg_cope on 2007-04-03
i have a laptop without a cdrom, only floppy.  i installed ubuntu on the hard drive by removing it and using another computer to install it to the HD.  i then put it back in the lap top it boots up but then stops.  is there any way to install ubuntu from the hd with a floppy??? or for that fact any other linux distro

---

### Post by matburton on 2007-04-03
Hmmm,

Well, if you do a bit of googling you may find a floppy that will allow you to then boot from a usb device (like a usb stick or cdrom). I'm assuming your computer can't boot from usb from the BIOS.

Otherwise (since I just posted this) you could look at this method
[[COLOR="Blue"]http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install[/COLOR]]("http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install")
which assumes you can boot from LAN.

Hope that helps :S

---

### Post by ramjet_1953 on 2007-04-03
Not a good idea to install this way.

Think about it. When you install any operating system, a major part of the install is detecting the hardware of the system you are installing it on and then the install is tailored to that hardware.

I'm afraid that you need to install it using the machine that it is going to be used on.

Regards,
Roger :cool:

---

### Post by seshomaru samma on 2007-04-04
ubuntu can recognise most new hardware on boot
when you change hardware you dont have to reinstall so it most likely that if you install ubuntu on a different machine and move it to a new box it would be ok
i would try to boot into rescue mode and then reconfigure x
```
dpkg-reconfigure xserver-xorg
```

---

### Post by Sef on 2007-04-04
If you follow seshomaru samma's advice, and it still don't work, then try the [Netboot Install]("https://help.ubuntu.com/community/Installation/Netboot?highlight=%28net%29%7C%28installation%29"), if the computer has internet access.

---

