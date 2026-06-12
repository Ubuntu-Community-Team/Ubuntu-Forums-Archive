---
title: "eMachine acting strange."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-03-13
I installed ubuntu on an eMachines computer and i'm having a few problems, 

#1: Nothing on the usb works, when i plug in my optical mouse the light on the bottom turns on so its getting power but ubuntu doesn't see it

#2: No audio works at all, the onboard is a AC '97 chip and it gives me nothing.  I installed a PCI one that i know nothing about and there is still nothing.

Onboard lan works just fine.  

Here is the lspci output

```

titan@dungeon:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
titan@dungeon:~$ 

```

PLEASE HELP! I have been at this for days and without sound i feel that my computer is useless...

---

### Post by drascus on 2008-03-13
This entry in Launchpad might be related to your computer...[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/175137](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/175137)
Posting some more information about your computer might also help people find solutions as well as posting what type of wireless optical mouse you have.

---

### Post by The Titan on 2008-03-13
> **drascus said:**
> This entry in Launchpad might be related to your computer...[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/175137](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/175137)
Posting some more information about your computer might also help people find solutions as well as posting what type of wireless optical mouse you have.
i would have loved to post more information but i dont have a clue what is causing the problem so i dont know what to post...  and its not a wireless optical mouse its just a cheap dell wired USB optical mouse with nothing on it but the letters DELL and 2 buttons.

---

