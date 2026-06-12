---
title: "Wireless adapter unworking"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by jgf621 on 2007-05-23
I have a fairly new HP laptop with a wireless device identified as Broadcom 802.11 b/g WLAN.  WINDOWS Driver is by BKK, name is BCMWL6.sys.  Is ther any way to make this work in UBUNTU 7.04?   I tried NDISWRAPPER in 6.10 previously without success.

All else, including Ethernet networking is fine.

Thanks.

---

### Post by jbrown96 on 2007-05-23
Wireless networking is very difficult in Linux, especially with broadcom chip sets. That is not to say it is impossible, it just takes some work. 
You should be aware that many of the security protocols that Wifi uses are also not supported. 

To solve your problem, we need to know what kind of wireless card you have. open a terminal (Applications->Accessories->Terminal) and type "lspci" without the quotes. Please paste the output here, and we can work from there.

---

### Post by jgf621 on 2007-05-23
Thanks.  Here it is.

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by freak101 on 2007-05-23
For many broadcom a working solution is fwcutter:
$ sudo apt-get install bcm43xx-fwcutter
$ sudo bcm43xx-fwcutter -w /lib/firmware/$(uname -r) bcmwl5.sys
$ sudo modprobe bcm43xx
$ iwconfig # check.

I found also this thread:
[http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom)
download and execute.. the quick way..

---

### Post by jbrown96 on 2007-05-23
I'm working on a guide, but I'm tired. Will post by 12:00pm central time tomorrow. sorry

---

### Post by jgf621 on 2007-05-24
I tried sudo bcm43xx-fwcutter -w /lib/firmware/$(uname -r) bcmwl5.sys and got following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcm43xx-fwcutter


Did I miss something?

Thanks.

---

### Post by jgf621 on 2007-05-24
Thanks to all.  I found my answer at [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990).

It worked first try.

Joe

---

