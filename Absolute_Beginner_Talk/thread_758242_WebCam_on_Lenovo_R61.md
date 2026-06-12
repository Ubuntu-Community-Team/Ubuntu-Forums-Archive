---
title: "WebCam on Lenovo R61"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by nhovan on 2008-04-17
trying to get my SXGA resolution webcam to work on my Lenovo R61. i am trying to use camorama. when i click on it. it says : Could not Connect to Video Device (/dev/video0) . Please check connection.

Anyone can help?

---

### Post by spiderbatdad on 2008-04-17
```
dmesg
``` may provide a link to sourceforge for updating the driver...or patching kernel modules.

---

### Post by aashay on 2008-04-18
Try modprobing the following modules:
```
sudo modprobe compat_ioctl32 uvcvideo videodev v4l1_compat  v4l2_common 
```
Try changing the order if you get any error
See if anything shows up in dmesg after you do this

---

