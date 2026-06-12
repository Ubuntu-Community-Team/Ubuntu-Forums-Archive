---
title: "A list of detected hardware ??"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Onesimus on 2007-04-05
I am using the LiveCD of Edgy 6.10, but before I go ahead with an full installation I would like to determine whether Ubuntu has detected all my hardware correctly.

Is there a simple method of looking at all the hardware devices that Ubuntu has detected ?

---

### Post by teaker1s on 2007-04-05
gnome has a hardware manager, but in terminal

pci
```
lspci
```
usb
```
lsusb
```:KS

---

### Post by xopher on 2007-04-05
Or for a really complete list (in terminal):

```
sudo lshw
```

---

### Post by Onesimus on 2007-04-05
Thanks for this - I will give it a try.  I am surprised that a list of the detected hardware is not more readily available (and that you have to be root to access it).

---

### Post by mikeyphi on 2007-04-05
> **Onesimus said:**
> Thanks for this - I will give it a try.  I am surprised that a list of the detected hardware is not more readily available (and that you have to be root to access it).
Don't know about the Live CD but once installed the info is available under SYSTEM - ADMINISTRATION - DEVICE MANAGER

---

### Post by jhenager on 2007-04-05
> **mikeyphi said:**
> Don't know about the Live CD but once installed the info is available under SYSTEM - ADMINISTRATION - DEVICE MANAGER

Right, and at the bottom is a button that will let you test the keyboard, mouse, network card, and video.
P.S. All these devices are working on my Dell XP system running 6.10 through VMWare.

---

### Post by alteredcarbon on 2007-04-05
I'm not sure how you're installing Ubuntu, but if you're taking the virtual machine route like I did, then be advised that despite all of your hardware working in the Live CD, if you install to a vm like I did, (Virtual/Box) then the hardware may not work after you install it.   Case in point:  Neither my sound card, floppy or USB are recognized by Ubuntu in the vm install despite having been recognized and working in the Live CD.

---

### Post by jhenager on 2007-04-09
> **alteredcarbon said:**
> I'm not sure how you're installing Ubuntu, but if you're taking the virtual machine route like I did, then be advised that despite all of your hardware working in the Live CD, if you install to a vm like I did, (Virtual/Box) then the hardware may not work after you install it.   Case in point:  Neither my sound card, floppy or USB are recognized by Ubuntu in the vm install despite having been recognized and working in the Live CD.

I guess this is one of those YMMV, because everything is running fine inside VMware except I couldn't get tricky and run Beryl - yet. :)

---

