---
title: "packet loss??"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by fenixfox on 2007-12-20
I have two computers hardwired to a netgear wirelss capable router here. Everything works fine on this machine (xp sp2) But on the one with unbuntu gutsy I seem to lose packets. I had xp on the exact same pc I now have unbuntu on and experienced no packet loss. Here are the stats on the pc using unbuntu:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] 182 SATA/RAID Controller (rev 01)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0b.0 Multimedia audio controller: Yamaha Corporation YMF-740C [DS-1L Audio Controller] (rev 03)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

Here are the ifconfig results on the pc using gutsy:
eth0      Link encap:Ethernet  HWaddr 00:01:6C:F7:72:5F 
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask: 255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3989 errors:157 dropped:0 overruns:0 frame:157
          TX packets:3193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3022731 (2.8 MB)  TX bytes:847090 (827.2 KB)
          Interrupt:22 Base address:0xdead

I can access only google via firefox and maybe two other sites. At first I thought it was firefox, but when I run update for unbuntu I get the failed errors for any update related to connecting to [http://archive.unbuntu.com](http://archive.unbuntu.com) gutsy/universal Translation-en_US

I have already disabled  ipv6 in gutsy and firefox as well to no avail. Strangely enough I can ping unbuntu.com with no errors as well as other sites. I have tried bypassing the router altogether as well. It has no special settings just a wep key so no one borrows my net.

---

### Post by fenixfox on 2007-12-20
bump

---

### Post by fenixfox on 2007-12-20
bump

---

### Post by fenixfox on 2007-12-20
anyone have any ideas?

---

### Post by The Cog on 2007-12-20
157 dropped packets - framing errors. I would normally suspect hardware problems for framing errors. Beyond that, I have no idea.

---

### Post by lintoon on 2007-12-20
I have to agree with The Cog and say hardware error.  Possibly protocol.  From what I remember (It's been a while) framing occurs at layer 2 which is responsible for converting data frames into bits for layer 1 (Physical) to process.  It also performs sychronisation and error correction of the frames so if you have a hardware error, eg faulty/loose network cable it's possible it could be reported as a framing problem.  Try a different cable.  Maybe try a different port on your switch.

There's always the possibility of protocol or driver problems.

---

### Post by fenixfox on 2007-12-20
I dont think its hardware. xp sp2 worked absolutely fine on the machine now running unbuntu. i tried using 5 different ethernet cables and hooked the modem right up to the machine. im going to try to find a driver for it on this windows pc and email it to myself.

---

### Post by lintoon on 2007-12-20
Well that kicks the hardware issue out of the window.  Unless by some uncanny, strange and weird coincidence your network card suddenly started packing up just at the exact same time you installed ubuntu :)

---

### Post by fenixfox on 2007-12-20
[SiS] 191 Gigabit Ethernet Adapter i could try reinstalling the sis 191 driver. (My wife mentioned trying it earlier but I wasn't listening). Could someone give me a step by step simple instructions for how to get the sis 191 driver for gutsy gibbon 7.10?  I need to download it onto a windows computer and email it to myself since I can only access google from the unbuntu computer.

---

### Post by fenixfox on 2007-12-20
bump

---

### Post by The Cog on 2007-12-21
If there's a problem with the driver, then there's a problem with the driver. Reinstalling drivers is a windows habit. You could try lookng to see if you can change settings like full/half duplex - they can cause framing arrors and others. OR try a different make of Ethernet adapter - they don't cost the earth.

---

