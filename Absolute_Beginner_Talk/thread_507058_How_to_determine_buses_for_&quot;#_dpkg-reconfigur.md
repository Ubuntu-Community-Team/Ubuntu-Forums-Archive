---
title: "How to determine buses for &quot;# dpkg-reconfigure xserver-xorg&quot;?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Githlar on 2007-07-22
I ran the reconfiguration utility for Xserver ("# dpkg-reconfigure xserver-xorg"). The utility told me that if I had two display adapters (which I do - one onboard and one PCI) I should specify the "BusID in an accepted bus-specific format." OK... how do I find that out?

Alternately, can't I just blacklist the onboard video(in /etc/modprobe.d/blacklist,) since I probably won't use it anyway? It works that way, right?

---

### Post by ReaderRat on 2007-07-22
You might try ```
lspci
```to see what you have.

---

### Post by Githlar on 2007-07-22
I did that and I didn't notice any buses? (Super n00b here...) How are the buses formatted? Or, rather, how can I format them in a way that X wants?

This is the example the XServer configuration gives:
SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000

I see nothing like that in lspci.

---

### Post by w4ett on 2007-07-22
do it again, and post the results...it will look like this:

> w4ett@w4ett-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondaw4ett@w4ett-desktop:~$ 

the Bus ID's are one the left of each line....

---

### Post by Githlar on 2007-07-22
Also, it appears in the XServer configuration that they are giving three different examples of buses? How do I know which to use?

Could you explain to me how to format those entries on the left properly for XServer?

PS: The specific bus that I'm trying to use is apparently 01:0a.0

It's funny though, I managed to use that number as a PCI address as 01:10:00 (converted from hex to decimal), however when I brought up my computer, I could hear the drums, but I couldn't see anything with my BIOS set to send video through PCI.

---

### Post by Githlar on 2007-07-22
Oh, wait a minute! I think I had this all wrong from the start! The ISA/PCI are some of the valid types! Stupid me! I can't believe that I was so stupid! Still, this resolution is hearbreaking. Now I know that my problem does not lie in the XServer configuration *sigh*. Stupid ATI cards...

---

