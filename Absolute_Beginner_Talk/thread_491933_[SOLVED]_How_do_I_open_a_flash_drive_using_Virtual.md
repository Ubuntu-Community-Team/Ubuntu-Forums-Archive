---
title: "[SOLVED] How do I open a flash drive using Virtualbox?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by waggygee on 2007-07-04
I installed windows XP using virtualbox, everything is fine but when I attempt to access my flash drive  I get this window pop-up saying 

Failed to attach the USB device (gives my device details) to the virtual machine (name of virtual machine.

Not permitted to open the USB device, check usbfs options.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

How do I permit it to open the USB device?

---

### Post by smoker on 2007-07-04
have a look at this page, it fixed it for me:
[http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices](http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices)

best of luck

---

### Post by waggygee on 2007-07-07
Cool! it worked for me too! Thanks!

---

