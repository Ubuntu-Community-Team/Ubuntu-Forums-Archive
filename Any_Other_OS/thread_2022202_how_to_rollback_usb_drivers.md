---
title: "how to rollback usb drivers"
date: 2012-07-10
forum: Any Other OS
---

### Post by jonmohr on 2012-07-10
I'm running linux mint, and up until today, I was able to access the internet through wifi through my netgear usb reciever. Today I logged on and I noticed that it wasn't working. a check of the system log showed that the kernel was repeatedly logging these two lines: Jul 10 13:35:15 jon-Satellite-L35 kernel: [  768.616121] usb 2-1: new full-speed USB device number 37 using ohci_hcd
Jul 10 13:35:15 jon-Satellite-L35 kernel: [  768.676152] hub 2-0:1.0: unable to enumerate USB device on port 1
the kernel also logs these lines when ANY usb device is plugged in.
I have absolutely no idea how to rollback or reinstall the drivers for the usb ports. how can i do this?

also, I have an atheros ar2314 built in wifi card, and the drivers are causing repeated errors in the tcp layer, which is why i had to use the usb network card in the first place. how would I fix this?

---

### Post by Perfect Storm on 2012-07-10
Moved to Other OS/Distro Talk.

---

