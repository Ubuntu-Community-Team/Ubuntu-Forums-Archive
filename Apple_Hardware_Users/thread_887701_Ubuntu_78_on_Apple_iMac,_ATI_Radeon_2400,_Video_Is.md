---
title: "Ubuntu 7/8 on Apple iMac, ATI Radeon 2400, Video Issues"
date: 2008-08-12
forum: Apple Hardware Users
---

### Post by macguitarman on 2008-08-12
Ubuntu 7/8 on Apple iMac, ATI Radeon 2400, Video Issues

Anybody know what gives here.

I have successfully installed Ubuntu 7 /8 on a Mac Pro with nVidia graphics and all is well, but essentially wasted a whole day trying to get either 7 or 8 to display properly on an iMac, ATI 2400.

Even when booting off the Ubuntu 7/8 CD, the graphics display drivers are a mess, with the iMac screen, mostly just going crazy, flickering, one can hardly make anything out to finish the install.

I have been through the whole apt get update ATI linux driver thing, and this seems like a crapshoot, still does not work, although you do get further,

the log in screen looks great, proper 1680 resolution, but when you log in, you get a white desktop screen, with nothing on the desktop, except the mouse pointer, this is when using version 8, rendering one stuck once again.

When using version 7, it's better but can not go past 1440 resolution, that the highest rez

At this point, if it is this hard, I'll just keep using Mac OS X, that takes me, 5 minutes to install an image with Super Duper and I am ready to do any video work.

Also looking at Ubuntu Studio 8x, but again I have no confidence that the ATI driver thing will work properly.

Any feedback greatly appreciated, thanks.

---

### Post by cyberdork33 on 2008-08-12
First, there are several "Ubuntu 7" releases. Please give the full release name you are referring to (i.e. Ubuntu 7.10 or the code name, Feisty Fawn).

Second, Please specify what iMac you are working with. There are Intel-based Macs and PowerPC-based Macs and they are very different beasts. Have a look though the "read before posting" thread linked in my signature to properly identify your Intel Mac version.

From what I can tell you are using an Intel iMac. It also sounds like you have not installed the proprietary ATI drivers, and rather have only installed the free ati driver. You should go to System > Administration > Hardware Drivers, and choose to enable the proprietary driver. If you have a problem being able to do that, you might want to look into using envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by macguitarman on 2008-08-12
> **cyberdork33 said:**
> First, there are several "Ubuntu 7" releases. Please give the full release name you are referring to (i.e. Ubuntu 7.10 or the code name, Feisty Fawn).

Second, Please specify what iMac you are working with. There are Intel-based Macs and PowerPC-based Macs and they are very different beasts. Have a look though the "read before posting" thread linked in my signature to properly identify your Intel Mac version.

From what I can tell you are using an Intel iMac. It also sounds like you have not installed the proprietary ATI drivers, and rather have only installed the free ati driver. You should go to System > Administration > Hardware Drivers, and choose to enable the proprietary driver. If you have a problem being able to do that, you might want to look into using envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

(Maybe not so Obvious) but an Intel iMac, 800 Mhz bus, dual 2 GHz Core 2 Duo

I am using 7.10, came with a Linux + magazine, and also trying 8.04 

Have already done all you suggested, still no dice, the issues are this

in 7.10, can only get max rez to 1440, you get a stretched picture

in 8.04, complete mess, as I described earlier

I performed the whole apt update get driver from ATI's site, but does not, work,

I'll try using Envy and thanks,

macguitarman

---

