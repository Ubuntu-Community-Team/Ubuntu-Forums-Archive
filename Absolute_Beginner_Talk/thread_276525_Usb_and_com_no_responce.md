---
title: "Usb and com no responce"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by computerlost on 2006-10-13
three day ago I bourgt a used compaq deskpro EN P33 and decided to install this os I Bought Online, well my printer won't, Usb, conected, work and none of my usb conections work either will my Palm connect via com port or usb How do I check them or where do I go for assistence.
   Today I feel very lost,

---

### Post by atomic drizzle on 2006-10-13
type lsusb. that will show u what usb ports r being used and by what. if system sees device, but doesnt know what to do with it, try googling the device to see if u need to download anything special to make it work.

---

### Post by 3rdalbum on 2006-10-13
For your printer, try [www.linuxprinting.org;](www.linuxprinting.org;) they have drivers. Also, in the Printing control panel, try selecting a different driver. For instance, if you had a Canon BJC-2100SP, and there's a driver for the BJC-2100 and the BJC-2000, and the 2100 driver doesn't work, then try the 2000 driver.

I'm having some trouble understanding what you're asking about the USB. Which devices aren't working?

There are heaps of programs available for Linux to work with Palm devices. Try downloading jpilot from the Synaptic Package Manager. You will probably need to enable the Universe and Multiverse repositories; instructions for this are here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

