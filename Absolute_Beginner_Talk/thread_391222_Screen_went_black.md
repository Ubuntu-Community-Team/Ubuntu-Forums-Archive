---
title: "Screen went black"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by jadda on 2007-03-22
Hi.
I was working on some documents for school when my laptop just died. The screen went black and the computer shut down. When I rebooted everything was as normal untill grub loaded. Then I got "Error message 22" and could not do anything. I rebooted with the live cd. I could not load any of partitions and gparted says my entire hd is unallocated. What happened and how can I fix it? Can I restore my HD with the live cd? I'm quite frustrated!

I had a dual boot with XP and ubuntu 6.10

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporind on 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6600] (rev a2)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
ubuntu@ubuntu:~$

---

### Post by zvacet on 2007-03-23
[http://ubuntuforums.org/showthread.php?t=370121&highlight=grub]("http://ubuntuforums.org/showthread.php?t=370121&highlight=grub")



[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub")

---

