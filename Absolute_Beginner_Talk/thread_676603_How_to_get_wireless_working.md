---
title: "How to get wireless working?"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by cragger on 2008-01-23
so first of all i guess you will need to know what wireless card i have so you can help me, 

well how do i find that out? sorry i am very new to the whole Linux system

---

### Post by CCNA_student on 2008-01-23
Try the command lspci in the terminal. It should show up somewhere in the output.

---

### Post by cragger on 2008-01-24
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by macogw on 2008-01-24
While attached to a wired internet connection, go to System -> Administration -> Restricted Driver Manager and install the BCM43xx firmware.


If that for some reason doesn't work or if you can't get that computer online at all to download, use whatever computer is online and download this: [http://macoafi.googlepages.com/firmware.tar.gz](http://macoafi.googlepages.com/firmware.tar.gz) then put it on the Desktop on your Ubuntu computer (transport using a flash drive).  To get the firmware into the right place, copy and paste these into the terminal one at a time:
```
cd Desktop
tar xf firmware.tar.gz
sudo chown root:root firmware/*
sudo mv firmware/* lib/firmware/

```
That will make root (admin) own all of the firmware in that tarball (that's like a zip) and then move them to /lib/firmware, which is where firmware goes.

---

### Post by cragger on 2008-01-24
ya i can get a wired conection but i want the wireless. i did enble the firmware in restricted drivers but that didnt seem to work. i will type in all of the wireless information and the click conect or w.e and it will just try to connect and nothing happens. i will try your sugestion when i get home, thanks

---

### Post by anewguy on 2008-01-24
Try following this link for your wireless card:

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")


:)

---

### Post by Lisa Y on 2008-01-24
> **macogw said:**
> While attached to a wired internet connection, go to System -> Administration -> Restricted Driver Manager and install the BCM43xx firmware.


If that for some reason doesn't work or if you can't get that computer online at all to download, use whatever computer is online and download this: [http://macoafi.googlepages.com/firmware.tar.gz](http://macoafi.googlepages.com/firmware.tar.gz) then put it on the Desktop on your Ubuntu computer (transport using a flash drive).  To get the firmware into the right place, copy and paste these into the terminal one at a time:
```
cd Desktop
tar xf firmware.tar.gz
sudo chown root:root firmware/*
sudo mv firmware/* lib/firmware/

```
That will make root (admin) own all of the firmware in that tarball (that's like a zip) and then move them to /lib/firmware, which is where firmware goes.

Will this firmware work if i have...or no??
06:00.0 Ethernet controller: Atheros Communication, Inc. AR5006EG 802.11 b/g Wireless PCE Express Adapter (rev 01)

---

### Post by Michl on 2008-01-24
Why do you need to know the wireless card you have.  I got wireless working without
knowing the name of the card.  I could be wrong, of course, but I would venture a
guess that your wireless problems have to do with setting-up networking.  The
problems I had had to do with that, but the solutions were all easy and straightforward.

what problems are you running into?

---

### Post by eluzi on 2008-01-24
For your wireless card u should follow this:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by cragger on 2008-02-15
so i kinda left this question for a bit but it is still now working, i enabled the firmware for my wirless in resticted drivers, im not sure if there is more to do than that, what else could i try to make it work?

---

