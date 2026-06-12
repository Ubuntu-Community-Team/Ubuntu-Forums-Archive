---
title: "hp dv6000 microdia webcam and usb mouse dying uvc and skype"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by thewump on 2007-11-13
I've seen various threads about periodically dying USB ports and if anyone is struggling with an HP laptop built in webcam issue with skype or dying usb mouse randomly or after hybernation then let me save you some time.

This is a WORKAROUND. If anyone knows what the real issue is, please help!  I've read on some threads that a bios upgrade fixes this, but bios upgrades without windows seem like a pain in the butt.

On my HP dv6000 laptop with skype, and microdia / uvcvideo drivers installed as found in other threads, when I use the camera the light comes on showing it is active, and there are no errors, but there is no picture.

The workaround is to restart the USB modules (* run as sudo )

modprobe -r ohci_hcd && modprobe ohci_hcd
modprobe -r ehci_hcd && modprobe ehci_hcd
modprobe -r uvcvideo && modprobe uvcvideo

Hope this saves some head bashing.

Keith

---

### Post by dannns on 2007-11-13
Thanks! I can finally use the camera on my HP DV6000Z. I made the following script to bypass the problem until it is solved.

```
#!/bin/bash
gksudo "modprobe -r ohci_hcd" && gksudo "modprobe ohci_hcd"
sleep 5
gksudo "modprobe -r ehci_hcd" && gksudo "modprobe ehci_hcd"
sleep 5
gksudo "modprobe -r uvcvideo" && gksudo "modprobe uvcvideo"
```

Is there a bug report about this?

---

### Post by thewump on 2007-11-13
I made that script too ;-)

I haven't made a bug report.. where would it be made?  I don't imagine HP give a toss.

Keith

---

### Post by sriram.sundar on 2008-01-27
Thanks for the tip! Worked like a charm on gutsy/dv6000z!

---

