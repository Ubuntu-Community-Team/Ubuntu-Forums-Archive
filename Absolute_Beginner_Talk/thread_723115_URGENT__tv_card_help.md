---
title: "URGENT : tv card help"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by blink_kid on 2008-03-13
hey im a newbie and i was wondering what should i do to run my tv card because im struggling with getting it to work ive downloaded tv time but it cant find my card and i dont know where to get drivers plz help anyone????

Thanks,
Blink_kid

---

### Post by handydan918 on 2008-03-13
A little actual information would help. What kind of TV card?

Open a terminal and do ```
lspci
``` and post the output back here.

---

### Post by blink_kid on 2008-03-13
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
 all the info plz help

---

### Post by blink_kid on 2008-03-13
the card is a flytv platinum33 running a phillis wdm silcone chipset notr sure whitch chipset though

---

### Post by handydan918 on 2008-03-13
I'm guessing that the secondary ATI card is your tv card? Have you enabled the restricted drivers repos and installed the ATI driver for it?

---

### Post by blink_kid on 2008-03-13
no i havent can u fill me in on hot to do that

---

