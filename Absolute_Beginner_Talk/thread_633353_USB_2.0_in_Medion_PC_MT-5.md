---
title: "USB 2.0 in Medion PC MT-5"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-12-06
I am running a file server on an old Medion PC MT-5 (P4, 2.5GHz, 512mb DDR RAM) connecting to my USB hard drive with USB 1.1. Obviously i would like a speed increase so i am trying to find out if the MT5 can support a USB2.0 PCI card. I have a spare card slot but i want to make sure the Mobo supports USB2.

Is there any way i can find this out without contacting the company (Form is massive and site doesnt look very active). 

There is a Microstar badge on the front of the case and from searching through a pile of German support forums i think the BIOS is Phoenix Bios D686. Is there a command i can run to find out if my Mobo supports USB2?

---

### Post by ymo on 2007-12-08
The lspci command will tell you if your computer has USB 2.0.
For example, on my Medion 8000XL (Model: PC MT6) I get:
```

$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:08.0 Communication controller: Intel Corporation 536EP Data Fax Modem
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)

```
As you can see, I have 3x USB 1 controllers (each runs 2 ports) and 1x USB 2 controller (which runs all 6 ports). If your controllers are not labeled USB 1 or USB 2 they may be described as OHCI or UHCI (USB 1) and EHCI (USB 2) 

If you do not have a USB 2 controller but you do have an empty PCI slot it should be easy and cheap to obtain a PCI USB controller card and fit it to your computer.

---

