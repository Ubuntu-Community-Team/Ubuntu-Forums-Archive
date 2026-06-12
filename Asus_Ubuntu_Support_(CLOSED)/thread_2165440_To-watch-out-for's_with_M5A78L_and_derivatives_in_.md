---
title: "To-watch-out-for's with M5A78L and derivatives in future 14.04-LTS?"
date: 2013-08-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by bcschmerker on 2013-08-05
I am currently looking over options for a new desktop system for [Microsoft® Windows® 8ight&#8482; 64-bit 8.1.12000]("http://windows.microsoft.com/") (MultiProcessor Kernel 6.3.9600), as ASUSTeK Computer, Inc., included too small a flash ROM on my CM1630-06's stock M5A78LT-M/CSM mainboard ([Advanced Micro Devices®]("http://www.amd.com/") Athlon II® X2 220 @ 2.80 GHz, 760G northbridge, SB710 southbridge) for the size of UEFI firmware necessary to support the new live boot feature for Win 8.  This means a new mission, as an Ubuntu® box, for the CM1630-06 (still running Microsoft® Windows® Se7en&#8482; Service Pack 1 7.0.8001, MultiProcessor Kernel 6.1.7601, as of August 2013), which has been upgraded with an EAH6850 DirectCU® video card (probable package: xserver-xorg-video-radeon), a XONAR® Essence&#8482; STX&#8482; audio card (probable package: linux-alsa-driver-modules-virtuoso), and Antec® power in the form of a TruePower® 750 Blue&#8482;.  My system has some upgradeability I have not yet exploited as of August 2013; AMD® manufactured several Socket AM3 MPU's, including Athlon II® X2's, X3's and X4's, and Phenom II® X2's, X3's, and X4's (I have no plans for an X6, as the lower maximum die temperatures would force repackage of the entire system in a Thermaltake® refrigeration-equipped full-tower case with Antec® TruePower® Quattro&#8482; 1200 PSU) that are supported in BIOS 0304.

At the current rate of development, I anticipate that Ubuntu® 13.11a1 Trusty Tahr&#8482; (the future 14.04-LTS) will pack a later LinUX Kernel series than 3.10 (released with 13.10 Saucy Salamander&#8482; and available for backport to 12.04.4-LTS Precise Pangolin&#8482;).  What software and driver issues with Advance Micro Devices® 64-bit hardware are still unresolved with no estimate for a fix, in terms of packages already supported by Canonical®?  This will give me enough lead time to raise, if necessary, any questions for the [LinUX Kernel Project]("http://www.kernel.org/"), [X Organization]("http://www.x.org/"), [Advanced LinUX Sound Architecture Project]("http://www.alsa-project.org/"), [Free Desktop Project]("http://www.freedesktop.org/"), &c.

---

### Post by bcschmerker on 2014-02-28
**Update:**  I ended up reinstalling Microsoft® Windows® 7.0.8001 (MultiProcessor Kernel 6.1.7601) due to uncommanded reboots on LinUX Kernel 3.13.0-generic (last-run package: linux-image-3.13.0-4-generic), so the Win6.3/8.1 search has been shelved for now.  Be advised that Kernel 3.13.0 can be panicky with certain hardware combinations - the UbuntuGNOME® trial revealed that a V4L2 crash (in my case, by attempting to force an unsupported resolution on my Logitech® QuickCam® S7500) was enough to trigger a reboot for kernel panic. ):P

---

