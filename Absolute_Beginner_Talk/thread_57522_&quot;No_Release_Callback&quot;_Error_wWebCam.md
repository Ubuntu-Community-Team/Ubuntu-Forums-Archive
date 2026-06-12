---
title: "&quot;No Release Callback&quot; Error w/WebCam"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-08-16
Still working on a webcam that is nominally supported, but problematic, I find the following error:

===========================================
Linux video capture interface: v1.00
drivers/usb/media/ibmcam.c: IBM PC Camera USB camera found (model 2, rev. 0x030a)
videodev: "ibmcam USB Camera" has no release callback. Please fix your driver for proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
drivers/usb/media/usbvideo.c: ibmcam on /dev/video0: canvas=352x240 videosize=352x240
usbcore: registered new driver ibmcam
usb 3-1: USB disconnect, address 2
drivers/usb/media/usbvideo.c: USB camera disconnected.
============================================
 I can't make any sense out of the linked article, but is this even an actual error?  The driver's in the kernel.

Is there anything else in here that would account for the problems and for programs being unable to find the device at /dev/video0?

Thanks for any help.

---

