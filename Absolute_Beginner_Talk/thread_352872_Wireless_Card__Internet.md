---
title: "Wireless Card / Internet"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by andtsoreyu on 2007-02-03
Well when I am in windows XP my wireless LED Light is working and on.  But when I am in ubuntu it isnt even on or working.

I have a 

Dell XPS M1210 

w/ an intel wireless card.


Any ideas on the steps I should take to get ubuntu to recognize my card and to get my wireless working?

---

### Post by %hMa@?b&lt;C on 2007-02-03
> **andtsoreyu said:**
> Well when I am in windows XP my wireless LED Light is working and on.  But when I am in ubuntu it isnt even on or working.

I have a 

Dell XPS M1210 

w/ an intel wireless card.


Any ideas on the steps I should take to get ubuntu to recognize my card and to get my wireless working?
please post the output of 
lspci 
and 
lsusb

---

### Post by andtsoreyu on 2007-02-03
I am guessing you want me to type those into the Terminal?

---

### Post by andtsoreyu on 2007-02-04
**lspci**
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
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
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d8 (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

**lsusb**
> 
Bus 005 Device 002: ID 046d:08c6 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  


---

### Post by H.E. Pennypacker on 2007-02-04
You'll see that your notebook's wireless card is called "Intel PRO/Wireless 3945ABG Network Connection."  Doing a forum search for "3945ABG," I was able to find the following:

[http://www.ubuntuforums.org/showthread.php?t=140085](http://www.ubuntuforums.org/showthread.php?t=140085)

[http://ubuntuforums.org/showthread.php?t=305662&highlight=3945ABG](http://ubuntuforums.org/showthread.php?t=305662&highlight=3945ABG)

For any other information, do the same search, and you'll find more.

---

### Post by appsmanster on 2007-02-09
> **andtsoreyu said:**
> Well when I am in windows XP my wireless LED Light is working and on.  But when I am in ubuntu it isnt even on or working.

I have a 

Dell XPS M1210 

w/ an intel wireless card.


Any ideas on the steps I should take to get ubuntu to recognize my card and to get my wireless working?

Run 'sudo network-admin' from the terminal. Is the wireless connection listed?

---

### Post by andtsoreyu on 2007-02-09
I figured it out.  I just went into the Applications

then add/remove and downloaded one of the wireless internet programs.


Works fine, didn't have to download driver or anything

---

