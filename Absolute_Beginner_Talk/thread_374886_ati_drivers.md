---
title: "ati drivers"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Art_Redwood on 2007-03-03
does ati make any Linux drivers for my vid card, I don't know what sort it is, (is there any way to find that as well), I running a 19 inch wide screen acer al1916w model, and Ubuntu can only give me at best a  1024 by 768,

---

### Post by Kateikyoushi on 2007-03-03
The following command will list your VGA.

```
lspci | grep VGA
```

If we know that then we can help with the installation.

---

### Post by scxtt on 2007-03-03
try running lspci:
```
[font=courier]scxtt@dreamlinux:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
[COLOR="DarkGreen"]01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850Pro]
01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850Pro] (Secondary)[/COLOR][/font]
```

---

### Post by mahy on 2007-03-03
> **Art_Redwood said:**
> does ati make any Linux drivers for my vid card, I don't know what sort it is, (is there any way to find that as well), I running a 19 inch wide screen acer al1916w model, and Ubuntu can only give me at best a  1024 by 768,

I'd advise you to look into your notebook specs. Anyway, you should install the following packages:

xorg-driver-fglrx
linux-restricted-modules-generic
linux-headers-generic

---

