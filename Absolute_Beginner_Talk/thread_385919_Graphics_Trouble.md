---
title: "Graphics Trouble"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-03-16
Disclaimer: I'm a complete graphics noob.  These questions are probably retarded.  Please don't hurt me.

I've got a Dell Inspiron 8600 laptop that's a few years old (2003 i think).  It's got an integrated 64mb graphics chip - I don't know much else about the graphics.  

I installed and launched nexuiz - but as soon as the client opens, my computer slows down to deathly slow.  It looks like I'm getting a frame rate around 1 frame per second or something.  Everything moves very slowly and the computer is nearly unresponsive.  It was very difficult to quit, but as soon as I did, the computer functioned normally.

Later, I tried to setup a screensaver.  Some of them work fine - however, most of them slow my computer down to slower-than-death the way nexuiz did.  

Like I said, I know very little about how graphics work.  Is it possible I need to install a special driver for my graphics chip?  Could something be wrong with opengl (I'm not entirely sure what opengl is, I think's its a library that's used to write most of the graphical software in ubuntu) and might I need to configure it?

As always, thanks for the help. :)

---

### Post by taurus on 2007-03-16
If you have a Dell, than chances are you are using one of those Intel onboard video controllers.  To be sure what it is, you can run this command from a terminal, Applications -> Accessories -> Terminal, to see what it is.

```
lspci
```
And if it's an Intel, then you probably need to use "i810" as a Driver in /etc/X11/xorg.conf.

```
cat /etc/X11/xorg.conf
```

---

### Post by atraeyu on 2007-03-16
> 00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)


Looks like nVidia to me:
> 
VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)


... any ideas what I can do to make it work correctly?

---

### Post by taurus on 2007-03-16
Yes, it is indeed nVidia.  Here's a guide to install a nVidia driver for it.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by atraeyu on 2007-03-16
Thanks so much.  It's working perfectly now.  :)

---

### Post by atraeyu on 2007-03-16
Thanks so much.  It's working perfectly now.  :)

---

### Post by taurus on 2007-03-16
You're welcome.

You're welcome.

---

### Post by atraeyu on 2007-03-16
Ooops, sorry for the double post.  Dunno how that happened. :)

---

### Post by taurus on 2007-03-16
I guess it's the echo.

---

