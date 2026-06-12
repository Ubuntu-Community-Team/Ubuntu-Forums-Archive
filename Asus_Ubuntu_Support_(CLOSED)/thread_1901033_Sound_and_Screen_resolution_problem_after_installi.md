---
title: "Sound and Screen resolution problem after installing Ubuntu"
date: 2011-12-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by rajesh1158 on 2011-12-27
**[SIZE=2]I recently installed Ubuntu on my machine. I found that audio was not working. Also i found maximum screen resolution to be 1024x768 while in Windows XP it was 1440x900. I'm using ASUS P5KPL-AM motherboard with[/SIZE][SIZE=2] Intel G31 chipset. I searched for drivers online but could not find. Please help. Below is the output of 'lspci' command:[/SIZE]**



~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by rajesh1158 on 2011-12-28
yay.....its working......I jus did the following steps:

typed the following command in terminal:

                                sudo gedit /etc/modprobe.d/alsa-base.conf


Then added the below line at the end of file:

                                 options snd-hda-intel model=generic

Then re-booted.

---

### Post by Hare Brain on 2011-12-30
Hi Rajesh. No I can't help. You sound like you have similar problems to me but much more technical knowledge so I want to be in on this thread.  I wouldn't know how to find out what hardware is in my son's new eeePC 1011PX, but I do know since I over-wrote Windows with Edubuntu 11.10 I can't figure out how to use the webcam and the volume controls don't work. So I'll watch and learn if that's OK?

---

