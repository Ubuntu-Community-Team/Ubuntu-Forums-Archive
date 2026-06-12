---
title: "Suse"
date: 2012-07-19
forum: Any Other OS
---

### Post by kasrawis on 2012-07-19
Can i install SUSE 12.1 in my laptop Acer 5732z as I'm facing problem with Ubuntu new versions with brightness

now I'm on Ubuntu 10.10 it's working fine just brightness is not adjustable  :KS

---

### Post by howefield on 2012-07-19
Thread moved to "Other OS/Distro Talk" forum.

---

### Post by cortman on 2012-07-19
> **kasrawis said:**
> Can i install SUSE 12.1 in my laptop Acer 5732z as I'm facing problem with Ubuntu new versions with brightness

now I'm on Ubuntu 10.10 it's working fine just brightness is not adjustable  :KS

It's a free world. Install whatever you want.
Not sure what you're asking here. If you need help installing openSUSE, go to the openSUSE forums. If you need help with the brightness adjusting, make a post on that with relevant information.

---

### Post by kasrawis on 2012-07-19
i've download and live CD Suse 12.1 after boot no screen lights too dark :( any ultimate solution ?

---

### Post by cortman on 2012-07-19
> **kasrawis said:**
> i've download and live CD Suse 12.1 after boot no screen lights too dark :( any ultimate solution ?

First, you need to specify whether you downloaded a trial of SUSE enterprise. or openSUSE.
If you're using openSUSE, there's an [excellent forums]("http://forums.opensuse.org/forum.php") devoted entirely to it, where you're much more likely to find help. If you're using SUSE enterprise, get in contact with SUSE support.
Good luck!

---

### Post by kasrawis on 2012-07-19
Laptop 

Acer Aspire 5732z
Intel Pentium Processor T4400 
3GB RAM
intel Graphic GMA 4500M upto 1308 MB DVMT

i want back light after installing either in ubuntu 12.04 or 
open Suse 12.1 please help 

i've searched the open suse forum couldn't find any help 
thanks for replying

---

### Post by ub07 on 2012-07-19
In Ubuntu, have you tried adjusting brightness in the settings manager? I'm in Kubuntu right now so I can't look it up exactly, but I know that there is a slider there where you can adjust the brightness.

---

### Post by Toz on 2012-07-19
Try using the kernel boot parameters:
```
acpi_osi=Linux acpi_backlight=vendor
```

As root, edit /etc/default/grub:
```
gksudo gedit /etc/default/grub
```
...and change the line that reads:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
...to read:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```

Save the file and run:
```
sudo update-grub
```

And reboot.

---

