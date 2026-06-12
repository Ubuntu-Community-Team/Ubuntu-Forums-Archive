---
title: "Crashing on bootup"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by GrahamNorton on 2006-10-17
I am an experienced Windows user, but a beginner at Linux so I am finding it hard to diagnose a problem I am having.

I just downloaded a copy of Ubuntu 6.06.1 and ran the install on my system using whatever was recommended (ie defaults). The installation went fine, however when the system booted for the first time in runs to the point where X Windows starts and stops.
 
The error states failed to start the X Server
"(ww) ATI: PCI Mach63 in slot 1:0:0 could not be detected
(ww) ATI: PCI Mach64 in slot 1:0:1 will not be enabled because it conflicts with another non-video PCI device
(EE) No Devices detected
Fatal Server Error:
No Screens found"

I have removed two PCI cards that are also in my system so that I just have my ATI X800 GTO PCIE video card with no change and I have reinstalled the system three times with different combinations of hardware and no luck.

My system specs are as follows...
AMD Althon 64 3000
1GB DDR400 RAM
40GB HD (plus three other Windows XP HDs)
ATI Radeon X800GTO PCIE w/256MB
CL Soundblaster Audigy 24
ATI TV Wonder Elite

The motherboard is using an ATI RS480 chipset with the BIOS date of Feb 06.

I have run Suse Linux 10.1 on the same machine without any problems, so I am puzzled as to why this problem is coming up. 

Any ideas anyone? Thanks.

Graham

---

### Post by bswilson on 2006-10-17
It sounds to me like Ubuntu does not have the proper drivers, or you selected a resolution and/or sync rates that aren't supported during setup.

How about posting the contents of your **/etc/X11/xorg.conf** file here, and maybe we can help by first getting you set up with a working GUI.  Then, we should also be able to help you get the right drivers.

---

### Post by GrahamNorton on 2006-10-19
Here is the file you mentioned. I hope you can help. Let me know if there is anything else you need.

Graham

---

### Post by GrahamNorton on 2006-10-30
To narrow down the problem...I got Ubuntu working with my integrated video card. However, when I try it with my ATI X800 GTO (PCI Express) card it comes up with the error message (as described in my previous post). Any suggestions?

Graham

---

