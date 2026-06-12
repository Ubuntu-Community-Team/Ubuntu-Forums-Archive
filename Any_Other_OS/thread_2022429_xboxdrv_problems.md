---
title: "xboxdrv problems"
date: 2012-07-10
forum: Any Other OS
---

### Post by tommywright on 2012-07-10
> **el_grimley said:**
> Hello

I've got an old xbox controller and a 4x xbox to 1x USB controller. I'm trying to get xubuntu 11.10 to recognise the controller, using [xboxdrv](http://pingus.seul.org/~grumbel/xboxdrv/). Unfortunately I get the bellow error. I've had a good look through a variety of websites as well as this one to try and solve the problem but I'm frankly a bit lost. Any thoughts as to what is going wrong.

```
xboxdrv 0.8.4 - http://pingus.seul.org/~grumbel/xboxdrv/ 
Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain 
conditions; see the file COPYING for details. 

Controller:        Microsoft Corp. Xbox Controller S
Vendor/Product:    045e:0289
USB Path:          008:004
Controller Type:   Xbox Classic

-- [ ERROR ] ------------------------------------------------------
 Error couldn't claim the USB interface: LIBUSB_ERROR_BUSY
Try to run 'rmmod xpad' and then xboxdrv again or start xboxdrv with the option --detach-kernel-driver.

```



I get the same here on Mint 11 with xboxdrv 0.8.2.

Controller:        Microsoft Xbox 360 Controller
Vendor/Product:    045e:028e
USB Path:          002:003
Controller Type:   Xbox360

-- [ ERROR ] ------------------------------------------------------
 Error couldn't claim the USB interface: LIBUSB_ERROR_BUSY
Try to run 'rmmod xpad' and then xboxdrv again or start xboxdrv with the option --detach-kernel-driver.

---

### Post by Perfect Storm on 2012-07-10
Split'n'move to Other OS/Distro Talk.

---

