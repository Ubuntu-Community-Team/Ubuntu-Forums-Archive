---
title: "Belkin RT61 Wireless"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by super.rad on 2007-03-16
I've just installed ubuntu 6.10 and cant work out how to connect to my wireless. its a belkin pci card. 
When i type "lspci" in the terminal i get 
```
02:00:0 Network controller: RaLink RT2561/RT61 802.11g PCI
```

and when i type "iwconfig" i get 
```
wmaster0 IEEE 802.11g Frequency: 2.41GHz
                         RTS thr: off    Fragment thr= 2346B
           wlan0       IEEE 802.11g ESSID: ""
                          Mode: Managed Frequency 2.42GHz Access Point: Not-Associated
                          RTS thr: off  Fragment thr= 2346B
```

if anyone could point out what is wrong/how to solve it that would be great as im a complete linux newb and its getting annoying having to switch between xp and ubuntu to try and fix the problem

---

### Post by K.Mandla on 2007-03-16
I used to have a Linksys card with an RT61 in it. [This]("http://kmandla.wordpress.com/2006/12/17/ralink-rt61-edgy-and-nvidia-again/") is how I got mine going. It might be of some use to you as well.

---

### Post by super.rad on 2007-03-16
thanks i've had a quick read through this, but it appears i need an internet connection to download some files? is it possible to do this through windows then transfer them over using a usb stick?

---

### Post by K.Mandla on 2007-03-16
Yes and no. The important files are on the installation CD -- things like build-essential and unzip. You do need to be able to access the internet to download the firmware from the RaLink web site. So yes, you can just move the firmware and drivers across on a USB. But no, the packages that build those drivers are installable from the CD.

---

### Post by super.rad on 2007-03-17
sorry im slightly confused? so most the things i need are on the cd, except the firmware which i can download from windows and swap over using a usb stick?

---

### Post by super.rad on 2007-03-17
Sorry to double post but after reading other threads i have downloaded the newest driver (RT61_Linux_STA_Drv1.1.0.0.tar) could somebody please just tell me how i install this driver in ubuntu.

---

