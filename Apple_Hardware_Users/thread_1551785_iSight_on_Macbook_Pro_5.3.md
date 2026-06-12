---
title: "iSight on Macbook Pro 5.3"
date: 2010-08-12
forum: Apple Hardware Users
---

### Post by gast0r on 2010-08-12
I recently installed Ubuntu 10.4 and completely removed Snow Leopard. After getting everything working, it was perfect. ISight worked perfectly fine until I turned it on the next day to realise that it no longer worked. 

Any suggestions?

Thanks.

EDIT:

After downloading the iSight firmware and using 
```
  sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport 
```to extract it and patch it, then shutting down and rebooting, it still isn't working. This also seems to cause Ubuntu to try and go into Low Graphics Mode. This was fixed after a restart.

EDIT: after using this guide:
> After beating my head against the wall ](*,)for the last few days on this problem I actually think I've got the solution. It works even after a reboot:grin:

(1) Extract the isight driver and use ift-extract-firmware tools. See [this]("http://ubuntuforums.org/showthread.php?t=1259166") and [this]("http://ubuntu-tutorials.com/2008/11/03/enable-apple-isight-camera-ubuntu-810/") for more info about installing and using the tool.
If you get an error like "no valid driver found" you'll need to find an older AppleUSBVideoSupport.

(2) In the /etc/default/acpi-support file, find MODULES and make it MODULES="isight_usb"

(3) Modify the file: /etc/udev/rules.d/isight.rules to be:
ACTION=="add", SYSFS{idVendor}=="05ac", SYSFS{idProduct}=="8507",  RUN+="/usr/lib/udev/ift-load --firmware /lib/firmware/isight.fw"

Step 1 sets up the isight driver. Step 2 seems to fix the /dev/video0  problem. Step 3 changes the Product ID to 8507 from the default 8300  which is incorrect. Skype, cheese, and gstreamer-properties can now find  the camera.Skype now recognises that isight is in fact, there and offers it as the only choice of camera to use. However, when I click the test button nothing happens.

EDIT:

Earlier today Skype and Cheese were recognising there was a camera. The visuals for both were black, however when I took pictures with Cheese, the picture was successfully captured. Also, the green iSight light was on. Now however, it has reverted back to not working.

---

### Post by gast0r on 2010-08-16
..Help anyone?

---

### Post by vongrippen on 2010-08-25
I have the same problem.

To deal with it, I had to switch from using the current kernel (2.6.32-24-generic) to one version back (2.6.32-23-generic). Once I did that it worked again. Seems to be some sort of regression in video4linux, uvcvideo, or the kernel. Haven't had time to work on a bug report yet...

Anyways, hope this helps!

---

### Post by gast0r on 2010-08-25
Ahh, hopefully this will be fixed soon. It seems to be a growing problem. And yeah, that was a good help. I know where to look for the problem now. Cheers.

---

