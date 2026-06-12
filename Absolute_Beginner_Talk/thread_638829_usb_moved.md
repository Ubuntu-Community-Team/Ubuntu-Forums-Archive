---
title: "usb moved???"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2007-12-12
Hi there,
I've just added a usb card and now I cant see my webcam on the existing usb?  is there some way to rescan the usb ports or something??

---

### Post by meborc on 2007-12-12
if you disconnect the webcam and connect it again, is there a change in **sudo lsusb** output?

---

### Post by tony.morse on 2007-12-13
no change.  It is listed, and as an audio device it is found and working but all image stuff says device not found, where before it all worked???

---

### Post by tony.morse on 2007-12-17
So before, my usb webcam worked, then I added a DVB card (which is a USB bus in the shape of a PCI).  Now the mic works on my webcam, it's listed correctly, it's found, but no application can find it?  Any ideas???

---

### Post by tony.morse on 2007-12-23
Ok some developments...

firstly there is no video anything in the /dev/ folder and the error I get with webcam applications is /dev/video0 not found.

Secondly, in my hardware device manager my webcam shows as attached to a usb 1.1 but actually it should be in usb 2.0 (I think?)  so perhaps adding the tv card (which is usb 2.0 has set the other system to usb 1.1??

please help

---

