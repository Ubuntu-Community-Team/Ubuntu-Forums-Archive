---
title: "Wireless stops when Idle."
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by cabal2000 on 2008-04-01
I just installed a Netgear router with wireless for my laptop. 
With 128bit encryption on the connection deads if I am not using it.
Without encryption on its doesn't.
Is there a setting that maybe turned on that would cause a does connect if idle?

---

### Post by mick8985 on 2008-04-01
can you show me the ouput of lspci?

---

### Post by cabal2000 on 2008-04-01
Sorry, I am very new to Linux.
What is lspci?

---

### Post by mick8985 on 2008-04-01
Applications > Accessories > Terminal

Type lspci

it will spit out all the devices attched to ur computer through pci, ls lists all files in a folder, lspci lists all devices on pci, lsusb lists all usb devices. You'll pick it up.
I asked for you to copy and paste the output of lspci just so I know which wireless card you have :)

---

### Post by cabal2000 on 2008-04-01
edwards@edwards-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
edwards@edwards-laptop:~$

---

### Post by mick8985 on 2008-04-01
Broadcoms are very problematic cards, unfortunately broadcom hates freedom.
This howto is very challenging for someone not used to command line.
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")
Hang tight I will see if i can find an easier way for you.

---

### Post by mick8985 on 2008-04-01
Yikes, unfortunately the easy way comes with a rather off putting disclaimer
[http://ubuntuforums.org/showthread.php?t=405990&page=101]("http://ubuntuforums.org/showthread.php?t=405990&page=101")
You could try using that program with the online installer, but I would recommend following the first guide, follow it step by step, putting each line into the terminal one at a time, and read it all very carefully. Jumping in at the deep end can be a fun experience, and will teach you alot. My first linux install was gentoo, which you compile from source code entirely through the terminal with no installer. I say go for it, worst comes to worst you might have to reinstall ubuntu.

edit: i just realised how poorly formatted that tutorial is, line by line deinfately isnt the way to go, to find out whether the it is actually the end of the command triple click highlight the command, that will show you what is intened to be all one line.

---

