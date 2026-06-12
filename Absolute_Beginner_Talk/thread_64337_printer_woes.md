---
title: "printer woes"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by barandis on 2005-09-10
Hi all, I have been having problems getting my printer (HP color laserjet 2500) to play nicely. I have got it installed and sitting in the printer section but it is trying to print to a serial port even though it is being detected from the command line as a usb device. I have been told in another general linux forum that I need to compile USB/serial support in the kernel. The howtos in the ubuntu wiki referring to tinkering with the kernel quite frankly terrify me. Is there an easy way? Any help will be greatly appreciated.
Cheers Bill

---

### Post by mlomker on 2005-09-10
Huh?  Is it a USB printer?  I have my 1012 working just fine.  I run KDE so things may be a little different in printer setup, but I assume you have to chose how it is connected when you set it up in the printer applet.

After plugging in the usb type **dmesg** into a terminal prompt.  It'll tell you want port it is connecting the printer as.  For example:

```
usb 1-1: new full speed USB device using ohci_hcd and address 6
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 6 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0D17

```

Mine is on /dev/usb/lp0.  When you go to configure the printer in the control panel it should ask you at some point where the printer is...that's what you'll want to point it to.

---

### Post by barandis on 2005-09-10
It didn't ask me where it was but after detecting it for the fifth time when I removed it and added it again it finally decided to work. I think my machine is just female and it's the time of the month.
cheers for the help

---

