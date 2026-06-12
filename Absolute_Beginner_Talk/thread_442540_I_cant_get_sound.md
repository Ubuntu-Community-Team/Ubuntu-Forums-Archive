---
title: "I cant get sound?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by gth835x on 2007-05-13
I have a built in sound card  and I cannot seem to get it to work since I switched from windows.  Is there a site I can go to that will help me trouble shoot it and then download the right driver maybe?

---

### Post by overdrank on 2007-05-13
> **gth835x said:**
> I have a built in sound card  and I cannot seem to get it to work since I switched from windows.  Is there a site I can go to that will help me trouble shoot it and then download the right driver maybe?

Hi can you tell us which version of ubuntu you are using and what sound card you are trying to use? You can find your sound card with the lspci command in the terminal.

---

### Post by beorn! on 2007-05-13
the quickest fix is usually to open a terminal, type, "alsamixer" and make sure the external is not muted. the "m" button will unmute any of the channels.... if that doesn't work reply to quad capps, and we'll go from there.

---

### Post by gth835x on 2007-05-13
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 05)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 05)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

