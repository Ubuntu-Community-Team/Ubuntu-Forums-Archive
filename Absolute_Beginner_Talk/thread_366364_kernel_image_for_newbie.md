---
title: "kernel image for newbie"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-02-20
I bought an airlink awll3026 usb wireless adapter because it was listed as supported "out of the box" with edgy. So I went ahead and blacklisted the internal broadcom driver that loads for my built in wireless card, which I had working (very slowly) with ndiswrapper and plugged in my new usb adapter. Well it saw it, but no load up at reboot, not even with network-manager installed. So I did some research and it seems that the support for the cards chipset, which is listed as: Bus 005 Device 002: ID 0ace:1215 ZyDAS, is in a different kernel image? I do not know how to get a more advanced kernel installed nor do I have any clue about kernels. Can anyone walk me through this?

Thanks if you can help!

---

### Post by Bachstelze on 2007-02-20
We need to know which driver your card uses. Type *lsusb* in a terminal nd paste what you get.

---

### Post by esaym on 2007-02-20
Where did you get your info that it was a compatible card?  

Generally any card from here has 'native' linux support: [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

edit: 
Oh I just noticed that you were using usb.  I don't think madwifi works with usb.  Any reason why you have to use usb only?  If it is a laptop there are plenty of pcmcia and mini-pci cards out there with the atheros chipset :D

---

### Post by Ripfox on 2007-02-20
Bus 005 Device 002: ID 0ace:1215 ZyDAS 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  


thats the output

Thanks for the help

---

