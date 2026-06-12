---
title: "Kodak Cameras and Ubuntu"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by say592 on 2007-04-08
Appearently my kodak camera requires not only special drivers in Windows, but also its special app. Now, ubuntu picked the camera up, but failed at importing the photos or allowing us to use the SD card as a storage device. 

Any ideas how to get this to work? We still have a windows machine, but it would be more convenient to be able to get them to work this way!

---

### Post by AndyCooll on 2007-04-08
This is what resolved the same issue for me with my Kodak camera:

```
sudo gedit /etc/udev/rules.d/40-permissions.rules
``` 
Find line like this: SUBSYSTEM=="usb_device", MODE="0644"
Replace it with: SUBSYSTEM=="usb_device", MODE="0666"

:cool:

---

### Post by Pelekophori on 2007-04-08
This thread might help - it got my Kodak P880 going:

[http://ubuntuforums.org/showthread.php?t=340271&highlight=kodak](http://ubuntuforums.org/showthread.php?t=340271&highlight=kodak)

---

