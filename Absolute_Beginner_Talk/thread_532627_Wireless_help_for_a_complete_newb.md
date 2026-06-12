---
title: "Wireless help for a complete newb?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by KoalaKrisp on 2007-08-23
Hello and thanks for reading this.
I am really new to Ubuntu and am having trouble accessing the wireless internet I know is available in my household. I'm sorry to say I do not know where to start about fixing the problem. I have a linksys router in my house (if that helps!). That is basically all the information I have- thank you very much for helping a huge newbie.

---

### Post by Paul133 on 2007-08-23
You have an internal wireless card? Then bring up a terminal (Applications > Accessories -> Terminal) and type ```
 lspci 
``` Then post the output. This way, we can find out what wireless card you have and what the chipset is.

---

### Post by KoalaKrisp on 2007-08-23
i typed lspci into the terminal and got this response:
00:00.0 Host bridge: ATI technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies INC EXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00.14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-ISA bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Contoller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400- AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host Bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host Bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Dram Controller
00:18.3 Host Bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network Controller: BroadCom Corporation BCM4318 [AirForce One 54g] 002.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

Once again thanks- ps I unforunately had to type this (I thought it would be faster than transferring electronically) So I apologize for any typos but I don't think there were any.

---

### Post by neoguy2012 on 2007-08-23
ooo broadcom cards... they're always a problem.  Try the following guide:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by likemindead on 2007-08-23
Follow [this thread]("http://ubuntuforums.org/showthread.php?t=405990") exactly and you'll be sorted in no time!

---

### Post by KoalaKrisp on 2007-08-23
I officially love both of you for your help! Thank you so much- the link you provided solved my problem pronto. I don't know how I would have ever gotten internet otherwise. Thanks agian.

---

