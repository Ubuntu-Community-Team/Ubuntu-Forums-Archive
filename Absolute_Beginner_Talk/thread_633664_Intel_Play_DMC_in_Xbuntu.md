---
title: "Intel Play DMC in Xbuntu"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by videogamer2791 on 2007-12-06
I have recently upgraded from XP to Xbuntu, because I know it is much better.  
I love it because of its superior plug and play, but I cannot seem to find a driver for my Intel Play Digital Movie Creator web cam.  Is there a way to manually install it, or make a driver of my own?

Thank you.

---

### Post by videogamer2791 on 2007-12-08
bumpty

anyone?

---

### Post by tgalati4 on 2007-12-08
Assuming this is a USB webcam, immediately after plugging it in, post the output of:

>dmesg | tail

---

### Post by videogamer2791 on 2007-12-08
thank you for your reply

dmesg | tail output:
```
[  581.540000] usb 1-1: configuration #1 chosen from 1 choice
[  591.876000] usb 1-1: USB disconnect, address 6
[  592.872000] usb 1-1: new full speed USB device using uhci_hcd and address 7
[  593.080000] usb 1-1: configuration #1 chosen from 1 choice
[  616.068000] usb 1-1: USB disconnect, address 7
[  617.820000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[  618.024000] usb 1-1: configuration #1 chosen from 1 choice
[  971.392000] usb 1-1: USB disconnect, address 8
[  974.152000] usb 1-1: new full speed USB device using uhci_hcd and address 9
[  974.360000] usb 1-1: configuration #1 chosen from 1 choice
```

---

### Post by videogamer2791 on 2007-12-09
So what do I do now with this information?

---

### Post by tgalati4 on 2007-12-10
Well according to your lsusb you have a:

I used lsusb its output was:
Intel Corp. Digital Movie Creator
which is obviously what I need, but the actual webcam is not working

A simple google search turned up: (The first entry)

Does the camera work on an Apple Macintosh* computer or a Linux* computer?
The Intel® Play&#8482; Digital Movie Creator is not supported on an Apple Macintosh* computers or a Linux* computer. There are no plans to add support for other operating systems. Intel has discontinued all Intel® Play&#8482; Toys in March 2002. Thus, no further development or updates will be made for this product.

It also shows up on a list of hardware for linux "orphans"

[http://hardware4linux.info/type/153/](http://hardware4linux.info/type/153/)

So I am guessing that it's an old piece of hardware that Intel stopped supporting in 2002.  Save your pennies for something newer and something compatible.

---

### Post by videogamer2791 on 2007-12-10
oh well, I thought that since it noticed what the hardware was, I had a chance.  I'll save up some money for a camera that I know will work.  Thank you for your help.

---

