---
title: "Scanner gone from applications"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-06-19
My USB HP 3970 scanner is listed in the device manager.  However, in xsane, gimp and open office it is not listed as an available device.

I thought that I would remove xsane and then reinstall to see if this helps but since this appears to take out the ubtuntu desktop as well I thought perhaps not .....  So I removed Sane only and then reinstalled.

When I then opened xsane this gives the following message - 

Failed to open device "hp3900:libusb:005:002"  Access to resource has been denied.

I guess this is the problem but I have no idea how to fix it ....

---

### Post by expatCM on 2007-06-22
I have discovered that if I launch xsane from a command prompt having first logged in as su / root that the scanner is detected and works with xsane as it should.

So I guess this is a permissions issue related to the hardware device (if permissions are set to hardware devices).  Still no idea how to fix it though.

---

### Post by expatCM on 2007-06-24
Well the cause is known but not the real solution....

I just booted to 2.6.20-15 and yes, the scanner and xsane are both there and work.

It seems to suggest that I need to wait for either an xsane patch or a new kernel upgrade. I am not good at waiting.

So back to the 2.6.20-16 and I installed Kooka. Not yet tested thoroughly but it seems to work well.

---

