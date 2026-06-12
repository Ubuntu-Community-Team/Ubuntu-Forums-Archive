---
title: "Wireless Router Setup Please"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by lookmomimonlinux on 2007-11-13
I just bought a wireless router and made all the right connections i just have to configure ubuntu to pick this up i imagine, what do i do from here?

---

### Post by poudin on 2007-11-13
run lspci at the command line...see what model your wireless network adaptor is....then look for a linux driver or use ndiswrapper to use the XP driver...

is this a laptop or desktop we are taking about...if laptop...check out [www.linlap.com](www.linlap.com) and search by vendor for help.

hope this helps.

---

### Post by lookmomimonlinux on 2007-11-13
what is ndiswrapper?

---

### Post by eldepeche on 2007-11-13
Wait, are you saying you have the router configured (and can connect using some other operating system) and want to know how to get your computer's wireless connection working?

> **lookmomimonlinux said:**
> what is ndiswrapper?

ndiswrapper is a compatibility layer that allows some wireless NICs that lack native Linux support to be used by wrapping the Windows driver into a fake Linux driver, essentially. It is only to be used if your hardware is unsupported by other means.

---

### Post by lookmomimonlinux on 2007-11-13
I had the cable modem connected to the wireless router and the router running to my pc and i had no signal. how do i make it work?

---

### Post by lookmomimonlinux on 2007-11-13
i am using ubuntu and what is a "compatibility layer"?

---

### Post by eldepeche on 2007-11-13
> **lookmomimonlinux said:**
> i am using ubuntu and what is a "compatibility layer"?

The driver for Windows won't work on Linux, because they use completely different programming interfaces. But, since it is known how to write a kernel module for Linux, and how to write a wireless driver for Windows, sometimes a Windows driver can be made to work on a Linux kernel by "wrapping" it. ndiswrapper essentially translates Linux wireless network configuration information into a form the card can understand, using the dictionary provided by the Windows driver. But this only works if the dictionary has enough words in it, so to speak.

Anyway, what is important is that you have a wireless NIC and a computer you want to use it with. Is it a PCI card you installed inside a desktop case, or a PCMCIA card, sometimes called a PC-Card, that you stick in a slot on your laptop? What is the model number?

---

### Post by lookmomimonlinux on 2007-11-13
i didn't install anything inside of the computer. i just entered ndiswrapper in a terminal and it said "The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common" do i want to do this?

---

### Post by eldepeche on 2007-11-13
Do you know what wireless networking hardware you have? If not, run 
```
lspci
```
and post the output here.

---

### Post by lookmomimonlinux on 2007-11-13
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by lookmomimonlinux on 2007-11-13
what am i supposed to do with my wireless networking hardware?

---

### Post by eldepeche on 2007-11-14
It doesn't look like you have any. Is this a laptop? Can you post the output of 
```
lsusb
```

---

