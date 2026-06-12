---
title: "Wireless Networking problem with Insipiron 1401 Laptop."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by esc0587 on 2007-04-19
I am a beginner who has just started using Ubuntu 6.10 on my Dell Inspiron 1401 laptop.  The problem is that it won't connect or find any signal.  I was wondering if I had to get certain drivers, if so what drivers.  Pretty much what I want is step by step set of  instructions on how to get connected.  I've been trying to install drivers, but I have no idea on how to put the commands in.  I get the % symbol by some lines but don't know what it means, if I should put the command in as root or put the % symbol in.  Please Help!!!

---

### Post by lamalex on 2007-04-19
can you paste the output of lspci?
put that command into the terminal and paste the output here, wireless usually needs some setup.

---

### Post by esc0587 on 2007-04-20
student@student-laptop:~$ ispci
bash: ispci: command not found
student@student-laptop:~$ lspci -v -t
-[0000:00]-+-00.0  Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
           +-02.0  Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
           +-02.1  Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
           +-1b.0  Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller
           +-1c.0-[0000:0b]--
           +-1c.1-[0000:0c]----00.0  Intel Corporation PRO/Wireless 3945ABG Network Connection
           +-1c.3-[0000:0d-0e]--
           +-1d.0  Intel Corporation 82801G (ICH7 Family) USB UHCI #1
           +-1d.1  Intel Corporation 82801G (ICH7 Family) USB UHCI #2
           +-1d.2  Intel Corporation 82801G (ICH7 Family) USB UHCI #3
           +-1d.3  Intel Corporation 82801G (ICH7 Family) USB UHCI #4
           +-1d.7  Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller
           +-1e.0-[0000:02]--+-00.0  Broadcom Corporation BCM4401-B0 100Base-TX
           |                 +-01.0  Ricoh Co Ltd Unknown device 0832
           |                 +-01.1  Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
           |                 +-01.2  Ricoh Co Ltd Unknown device 0843
           |                 +-01.3  Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter
           |                 \-01.4  Ricoh Co Ltd xD-Picture Card Controller
           +-1f.0  Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE
           \-1f.3  Intel Corporation 82801G (ICH7 Family) SMBus Controller
student@student-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
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
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
student@student-laptop:~$

---

