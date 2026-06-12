---
title: "iSight"
date: 2009-08-21
forum: Apple Hardware Users
---

### Post by NielsAMD on 2009-08-21
Hello,

I have had some trouble getting the iSight of my macbook to work on my Ubuntu 9.04 Jaunty OS.
When i try to use the i sight firmware extractor tool, it cant find the firmware file.
I followed these instructions:[https://help.ubuntu.com/community/MacBook3-1/Jaunty](https://help.ubuntu.com/community/MacBook3-1/Jaunty)

Can someone help me?

Thanks,
Niels

---

### Post by produnis on 2009-08-22
Try this:

mount your Mac-HDD (in your GNOME-panel, you find it clicking "Places").

Open a terminal and type in:
```
cd /media
ls

```there you should see the Mac-partition now.

The firmfare is on this partition in folder
```
/System/Library/Extensions/IOUSBFamily.kext/Contents/Plugins/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
```Well, if you start up isight-firmware-tools, it asks you where the firmware is, and it suggest the path 
```
/System/Library/Extensions/IOUSBFamily.kext/Contents/Plugins/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
```and here's the trick:
as the Mac-partition is mounted to /media/MAC  (where MAC is the name of your mac-hd)
you need to modify the path like this:
```
/media/MAC/System/Library/Extensions/IOUSBFamily.kext/Contents/Plugins/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
```should work then....

---

### Post by NielsAMD on 2009-08-22
Thank you, it worked!

---

