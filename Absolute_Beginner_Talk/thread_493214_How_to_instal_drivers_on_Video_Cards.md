---
title: "How to instal drivers on Video Cards?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by reynal_sf on 2007-07-05
Okay... here's the deal. My brother has 64MB of Video (Shared with RAM) and the games run very slow... (This did NOT happen with Windows XP) ...not even Ubuntu desktop effects work... what seems to be the problem? his on-board Video Card is a "SiS" (Silicon integrated Systems) I went to the website to look for drivers... but the driver compartible with the Video hardware it's only for Windows XP, what should I do? or... if it's not the driver... what should I instal?

---

### Post by Raineer on 2007-07-05
What games are you trying to run?  Desktop-effects needs 3D acceleration to work, which means you will need a proper driver for it.  

Have you tried:
```
sudo dpkg-reconfigure xserver-xorg
```
And looked through the list of drivers? You may find one that works better.

---

### Post by Seisen on 2007-07-05
Type this into a terminal and post it  here.

```
lspci
```

---

### Post by reynal_sf on 2007-07-05
Okay, I'm a total noob with Linux, where do I type those codes?

---

### Post by overdrank on 2007-07-05
> **reynal_sf said:**
> Okay, I'm a total noob with Linux, where do I type those codes?

HI in the terminal located under applications,accessories, terminal. :popcorn:

---

### Post by reynal_sf on 2007-07-05
This is for the "lspci" code.

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by reynal_sf on 2007-07-05
These are the controllers for server X:

apm              &#8593;                                                         &#9474;   
ark              &#9646;                                                         &#9474;   
ati              &#9618;                                                         &#9474;   
cirrus           &#9618;                                                         &#9474;   
cyrix            &#9618;                                                         &#9474;   
chips            &#9618;                                                         &#9474;   
fbdev            &#9618;                                                         &#9474;   
glint            &#9618;                                                         &#9474;   
i128             &#9618;                                                         &#9474;   
i740             &#9618;                                                         &#9474;   
i810             &#9618;                                                         &#9474;   
imstt            &#9618;                                                         &#9474;   
mga              &#9618;                                                         &#9474;   
neomagic         &#9618;                                                         &#9474;   
newport          &#9618;                                                         &#9474;   
nsc              &#9618;                                                         &#9474;   
nv               &#9618;                                                         &#9474;   
rendition        &#9618;                                                         &#9474;   
s3               &#9618;                                                         &#9474;   
s3virge          &#9618;                                                         &#9474;   
savage           &#9618;                                                         &#9474;   
siliconmotion    &#9618;                                                         &#9474;   
sis              &#9618;                                                         &#9474;   
sisusb           &#9618;                                                         &#9474;   
tdfx             &#9618;                                                         &#9474;   
tga              &#8595;               
trident          &#9618;                                                         &#9474;   
tseng            &#9618;                                                         &#9474;   
vesa             &#9618;                                                         &#9474;   
vga              &#9618;                                                         &#9474;   
via              &#9618;                                                         &#9474;   
vmware           &#9646;                                                         &#9474;   
voodoo           &#8595;

---

### Post by Rohen on 2007-07-07
Hi all, I'm in the same bind here.  I'm trying to configure my video driver.  Whenever I play a movie full screen it looks all choppy.

How do I install the best driver?

:(

---

### Post by danielmendesleao on 2007-08-09
I'm have the same case here... in a Acer notebook. Exactly same video card. Note that there's a SIS option when selecting the driver in the list. That's whas my default option (never changed manually this). You consider VGA (thinking it's generic) better then the SIS driver ?

---

