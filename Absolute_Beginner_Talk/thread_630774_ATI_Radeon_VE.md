---
title: "ATI Radeon VE ?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by aaronbridge on 2007-12-03
I am an OpenSuse user, but I want my daughter to try Ubuntu. It installed fine, but it seems to me the video drivers may be incorrect.  Yes, there is video, I'm typing this from her computer.  However, when typing and when windows fade in and out it is choppy.  Video is the same way.  The video card is an ATI Radeon 7000.  THe card works great in OpenSuse, but OpenSuse calls the card an ATI Radeon VE.  I cannot find drivers on the ATI website.  Can anyone point me in the right direction to get the card working properly.

Thanks

---

### Post by Severun on 2007-12-03
There seem to be some issues with the fglrx drivers (ATI drivers) at the moment.

You choices for video no the ATI are:

vesa driver - 2D
fglrx - 2D Mode
fglrx - 3D Mode (I've been having problems on it w/ Gutsy and my ATI card)

I got my ATI card to work with an OK desktop in 2D by clicking on options in the lower left of the login screen, then select gnome failsafe.

I'm hoping the ATI drivers will be fixed soon.  There are also other options for drivers, but none of them are pretty.

You can get the fglrx driver by installing the restricted drivers package from the Synaptics Package manger or by using apt-get.

---

