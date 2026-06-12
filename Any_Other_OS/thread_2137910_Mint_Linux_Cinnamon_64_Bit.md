---
title: "Mint Linux Cinnamon 64 Bit"
date: 2013-04-22
forum: Any Other OS
---

### Post by gordie69 on 2013-04-22
Hey guys I have a friend that has a Acer laptop with a dual core AMD chipset 6 gigs of ram and decided to put Mint LInux Cinnamon 64 bit on instead of Windows 7 and everything he said works but when he goes in system settings and goes to input there is no web cam and he's trying to get his Skype working but theres seems too be no web cam I've helped him install it and did all additional drivers and did the wireless drivers and video but not sure how to get the web cam

---

### Post by tgalati4 on 2013-04-22
There are several applications that use the webcam.  See if they work.  Try opening *cheese*.

Open a terminal and post the output of:

```
lsusb
```

You should see some sort of webcam:

tgalati4@Mint14-Extensa ~/Desktop $ lsusb 
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

If not, then you will have to do some research to find what specific model of webcam is installed.

```
dmesg | grep webcam
```

tgalati4@Mint14-Extensa ~/Desktop $ dmesg | grep webcam
[    1.569008] usb 1-1: Product: Acer CrystalEye webcam
[   26.502332] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
[   26.509613] input: Acer CrystalEye webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input4

---

### Post by gordie69 on 2013-04-22
Thanks I'll try that I thought it should of picked up web cam due to laptop only 1 year old

---

### Post by Perfect Storm on 2013-04-22
Moved to Other OS/Distro Support.

---

