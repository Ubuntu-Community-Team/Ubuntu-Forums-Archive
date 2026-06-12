---
title: "USB DISK ON UBUNTU! Help!"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Khurrum on 2007-08-18
Hi, everytime I insert my flash drive on UBUNTU, the light on the flash drives turns on then goes of and I can't use it. HElp me pleaseee!


My USB drives work fine, they work great on WIndows, its just on Ubuntu thats the problem, could it be the flash drive isn't supported?



[  119.766222] usb 3-4: device descriptor read/64, error -32
[  119.982208] usb 3-4: device descriptor read/64, error -32
[  120.198197] usb 3-4: new high speed USB device using ehci_hcd and address 5
[  120.310189] usb 3-4: device descriptor read/64, error -32
[  120.526180] usb 3-4: device descriptor read/64, error -32
[  120.742169] usb 3-4: new high speed USB device using ehci_hcd and address 6
[  121.150142] usb 3-4: device not accepting address 6, error -32
[  121.262138] usb 3-4: new high speed USB device using ehci_hcd and address 7
[

These are the last few lines I get!

---

### Post by Dark Star on 2007-08-18
Have you treid it on other USB drives ? USB drive u plug work in other OS ? maybe the UBS hub may be defected :( So plz get it checked :D

---

### Post by scrooge_74 on 2007-08-18
after you plug it in

open a terminal and type dmesg

see if the last couple of lines say something about the usb drive

---

### Post by TheWizzard on 2007-08-18
please give the output of
```
lsusb
```
(when the usb is plugged in of course)

---

### Post by TheWizzard on 2007-08-18
> **scrooge_74 said:**
> after you plug it in

open a terminal and type dmesg

see if the last couple of lines say something about the usb drive


you can use grep to search for usb: 
```
dmesg | grep usb
```

---

