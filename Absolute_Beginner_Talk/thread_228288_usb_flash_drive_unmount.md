---
title: "usb flash drive/ unmount"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-08-02
When I unmount my usb flash drive (right-click on desktop icon/unmount) a light stays on inside it but yet the icon disappears on my desktop. Is there a problem unmounting or is this normal? I'm curious since the power light stays on inside my usb flash.

Erick

---

### Post by aysiu on 2006-08-03
It's normal. The light will go off only in Windows. My USB key's light stays on after ejecting whether I'm using my Ubuntu desktop or my wife's Mac Powerbook.

---

### Post by emprog on 2006-08-03
Great, thanks. I opened terminal and typed mount before and after unmounting and saw it no longer listed but was just wondering why the light stayed on. What worried me was the light goes out with windows like you said. Thanks again. By the way, my instructions talks about creating a mount point mkdir /mnt/usbdisk, then mount to it but I guess there is no need to perform that in Ubuntu?

Erick

---

### Post by mcduck on 2006-08-03
The difference is that when you 'safely remove' a device in Windows, windows cuts power from the USB port too. Linux leaves the power on. For example if I 'safely remove' my iPod in windows it stops charging, but in Linux I don't need to have it mounted as it will charge anyway :)

Linux actually works the way USB standard defines. USB ports should _always_ output 5V when the computer is on.

---

