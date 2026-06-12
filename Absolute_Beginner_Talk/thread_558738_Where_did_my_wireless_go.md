---
title: "Where did my wireless go?"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by TalioGladius on 2007-09-24
Apparently ubuntu doesn't even realize I have a wireless card in my laptop.  Network settings doesn't even have my wireless listed.

Dell XPS 1710 laptop

Searching around I see that an upgrade from the previous version of ubuntu caused some issues, but nothing on a fresh install.  Any ideas?

---

### Post by overdrank on 2007-09-24
> **TalioGladius said:**
> Apparently ubuntu doesn't even realize I have a wireless card in my laptop.  Network settings doesn't even have my wireless listed.

Dell XPS 1710 laptop

Searching around I see that an upgrade from the previous version of ubuntu caused some issues, but nothing on a fresh install.  Any ideas?

Hi can you post the output of the command 
```
lspci
```
This will help us identify your wireless adapter
Us that command in the terminal,the terminal is located under applications, accessories.

---

### Post by TalioGladius on 2007-09-24
> **overdrank said:**
> Hi can you post the output of the command 
```
lspci
```
This will help us identify your wireless adapter
Us that command in the terminal,the terminal is located under applications, accessories.

Sure, here it is.


:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by overdrank on 2007-09-24
Hi after searching some, have activated the restricted drivers manager located under system,administration?

---

### Post by TalioGladius on 2007-09-24
> **overdrank said:**
> Hi after searching some, have activated the restricted drivers manager located under system,administration?Yes, it has the intel pro/wireless 3945 network connection driver for linux enabled and in use.  The other ones listed are nvidia and three for vmware, all enabled and in use.

---

### Post by overdrank on 2007-09-24
> **TalioGladius said:**
> Yes, it has the intel pro/wireless 3945 network connection driver for linux enabled and in use.  The other ones listed are nvidia and three for vmware, all enabled and in use.

Ok and you have rebooted the system since the activation and it is not showing in the system,administration, network?

---

### Post by TalioGladius on 2007-09-24
> **overdrank said:**
> Ok and you have rebooted the system since the activation and it is not showing in the system,administration, network?Actually I don't believe it's been in there since the install.  I don't remember even having to enable it in the activation.  I've rebooted many times since then.

---

### Post by TalioGladius on 2007-09-24
bump

---

