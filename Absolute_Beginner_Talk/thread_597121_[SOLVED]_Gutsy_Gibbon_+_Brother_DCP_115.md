---
title: "[SOLVED] Gutsy Gibbon + Brother DCP 115"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-10-30
I am having the (unfortunatly) all too common problem getting my printer to work under Ubuntu, this has been a major pain point for me and from forum evidence many other ubuntu users...

I own a Brother DCP 115 printer, which until recently has worked (with a little work and help from forum members) under all previous Ubuntu versions, upon doing a complete reinstall of Gutsy I was happy to find that Gutsy recognised my printer automatically as a Brother DCP 115 and also set a recommended driver....fantastic!

Its now the time when I print my first doc and low and behold, the printer receives the doc, however nothing prints...

I remember that when setting up a usb printer in feisty the following entry had to be placed within the fstab doc:

```
none /proc/bus/usb usbfs auto,devmode=0666 0 0
```

Followed by mounting and un mounting the usb device in the terminal:

```
sudo umount /proc/bus/usb
sudo mount /proc/bus/usb
```

This has been done to no avail.....

any hints, tips, or reports of anyone getting this printer to work somehow in Gutsy??

---

### Post by TURNER on 2007-10-30
Resolved, many thanks to the thread: [http://ubuntuforums.org/showthread.php?p=3671326#post3671326](http://ubuntuforums.org/showthread.php?p=3671326#post3671326)

---

