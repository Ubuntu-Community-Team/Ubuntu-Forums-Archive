---
title: "external stick performance slow"
date: 2013-09-21
forum: Any Other OS
---

### Post by jj4 on 2013-09-21
I have Linux mint installed on a USB stick, which runs ok but occasionally slows/hangs for 30seconds before continuining.
I also run Win 7 off of VirtualBox. The Win7 is installed on an external hard drive connected via USB (the spinning kind).
I tried imaging the Win7 to another usb stick (high performance 32GB transcend usb 3.0) but when I ran it off that, via, VirtualBox, the performance was very slow.
They are both connected via USB so why is the external hard drive faster and doesn't show any performance issues?

---

### Post by howefield on 2013-09-21
Thread moved to the "Other OS/Distro Support" forum.

---

### Post by sudodus on 2013-09-21
Most pendrives have slow flash memory compared to a HDD, so that the flash memory will set the limit rather than the USB interface, even when it is the old USB 2 interface. Flash memory is particularly slow at the start and stop of each file, so read/write of many small files will be particularly slow. See this link [https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites) which also contains a link to a site evaluating USB pendrives.

I have USB 3 pendrives of two brands, Transcend and Sandisk Extreme, and the Sandisk pendrive is much faster, which is obvious in a USB 3 port. (Both pendrives are reliable and bootable.)

---

