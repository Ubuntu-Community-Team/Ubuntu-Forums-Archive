---
title: "Ubuntu 11.04 wont suspend"
date: 2011-09-13
forum: Asus Ubuntu Support (CLOSED)
---

### Post by You22211 on 2011-09-13
Hello everyone,

I'm fairly new to Ubuntu and just updated to 11.04 64bit. I'm using an Asus laptop(i5 2.5 ghz) 4 gigs of RAM.  Whenever I close the lid to my laptop, or tell it to suspend I get a black screen with the following message:

[ 76.067893] i2400m_usb 1-1.1:1.0: failed to suspend, will reset on resume
[ 78.849095] i2400m_usb 1-1.1:1.0: device rebooted: reinitalizing driver


Thanks for any help!

---

### Post by Toz on 2011-09-14
This sounds like it may be an issue with usb3 (known bug). Can you open up a terminal window, type in the following command, and post back the results?
```
ls /sys/bus/pci/drivers/ehci_hcd/
```

We can try unbinding these devices prior to suspend and rebinding on resume.

---

