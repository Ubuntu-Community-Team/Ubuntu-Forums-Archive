---
title: "Dell Inspiron 2200 - Wireless Optional?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by SlaughteredLamb on 2008-03-26
Don't hurt me, I am new here.  I am also a laptop noob, to boot.  My question is reasonably simple; how do I determine if my 2200 actually has a wireless called installed?  All indications on my end are that this laptop does not in fact have wireless capabilities, but I am still unsure of how to look for such things in Ubuntu.  For example...

lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

In other examples I have seen, the wireless adapter would be at position 2:03, but there is nothing there on mine.  So there stands my question.  How do I determine the existence of wireless card in my Inspiron 2200?  Did the above command already tell me what I need to know?

---

### Post by brownknight on 2008-03-26
I am a noob too and dont know the technical way but in my case, if the network manager icon on your top panel is picking up wireless networks - then you have it. :D or
  
lshw -C network

---

### Post by pseudo-random on 2008-03-26
Looking at that I can see a modem and an ethernet adaptor but no wireless. Sorry!

---

