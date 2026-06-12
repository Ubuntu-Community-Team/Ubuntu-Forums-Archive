---
title: "how do i mount flash card"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by humbll on 2007-03-10
i have a dell inspiron e1505 with edgy installed. my sis wants me to get her pictures off of a flash card from her camera, and i do not even know where to look for the card at. I assume i must mount it first. can anyone give me some pointers? the card is a Fujifilm xD Picturecard 128MB being plugged directly into my laptop, the card is small: about 1 inch wide and 3/4 inch deep, and 1/8(or less) thick

lspci output is: (the second to last device is my flashcard reader hardware)
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
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
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

and i do not see anything in /dev which shows me the card

---

### Post by fasoulas on 2007-03-10
Your flash card should be mounted automatically   It must be an icon on your desktop

---

### Post by dptxp on 2007-03-10
I have similar problem. My MMC card is not detected in the ACER 5101AN laptop though mounting of removable drives and media is enabled (by default, verified). The solution shall be same for MMC or COMPACT FLASH card.

---

### Post by humbll on 2007-03-10
> **fasoulas said:**
> Your flash card should be mounted automatically   It must be an icon on your desktop

no, i don't see any icons on the desktop for it...

---

### Post by computx on 2007-03-10
I did a quick google/linux search for R5C592 Memory Stick.
It seems that device is not supported in linux. Sorry.
The good news is for about $12 you can buy a pc-card or usb 6in1 media reader that is supported by linux.

---

### Post by oilchangeguy on 2007-03-10
i use a usb media card reader, and when i plug it in, it shows up as an icon on the desktop. however in your case, it's built in. try going to system, admin, disks. it should show up there.

---

