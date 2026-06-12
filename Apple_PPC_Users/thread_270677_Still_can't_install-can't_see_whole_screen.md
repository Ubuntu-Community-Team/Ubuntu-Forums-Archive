---
title: "Still can't install-can't see whole screen"
date: 2006-10-03
forum: Apple PPC Users
---

### Post by Tunemonkey on 2006-10-03
I posted last week or so 

[http://ubuntuforums.org/showthread.php?t=265117](http://ubuntuforums.org/showthread.php?t=265117)

and I tried what was suggested. I still cannot get any resolution other than 640x480. That is my only choice in the screen resolution control panel when I start from the Ubuntu CD. I know that the CD is OK because I am able to proceed through the install on my G5, and I get the choice of 1024x768, 800x600, and 640x480.

I've changed my xorg.conf file in the Monitors section to what other have said worked for them. I logged out and logged back into Ubuntu and rechecked the xorg.conf file and it was indeed what I had saved it at which was to display "only" the native 1152x768 resolution of my Powerbook. No other resolution was listed in there. I still only had the 640x480 to choose from in the screen resolution control panel.

Might I need some ATI driver that I don't have? My graphics card says this;

Chipset Model:	ATY,RageM6
  Type:	Display
  Bus:	AGP
  Slot:	ATI
  VRAM (Total):	16 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x4c59
  Revision ID:	0x0000
  ROM Revision:	113-XXXXX-115

I even went through the xserver reconfig dialog (sudo dpkg-reconfigure xserver-xorg) and changed the HorizSync and VertRefresh rates to those recommended by others.

What to do now?

Also, I have a 5Gig partition on my Powerbook that I wiped OS 9 from. Can I use this for Ubuntu (if I ever get it installed). Will that partition show up when I get to that part of the installer, and do I have to format it other than Mac OS Extended?

Thanks for your time,

T

---

