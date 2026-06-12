---
title: "integrated mic + TV tuner card in lenovo y500"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by sameer.india on 2008-04-04
Well, guess ??

Yeah, how do you make them work?

---

### Post by sameer.india on 2008-04-09
No answers

---

### Post by wolfen69 on 2008-04-09
giving us more details about what mic and tv card you have would help.

---

### Post by sameer.india on 2008-04-10
I don't know they are integrated

---

### Post by GoCool on 2008-04-10
So what is your question?

---

### Post by smurphy_it on 2008-04-10
You should start by posting the output of the following commands:

lspci
lsusb

---

### Post by sameer.india on 2008-04-10
sameer@sameer-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
sameer@sameer-laptop:~$

---

### Post by sameer.india on 2008-04-10
sameer@sameer-laptop:~$ lsusb
Bus 005 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 002: ID 10fd:2535 Anubis Electronics, Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000

---

### Post by sameer.india on 2008-04-10
any solutions

---

### Post by sameer.india on 2008-04-11
Hello any answers?????????????????????????????

---

