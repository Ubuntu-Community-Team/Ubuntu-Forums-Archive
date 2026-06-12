---
title: "sound card problems?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by LostLake on 2007-10-28
I have been experimenting with various audio players and each have the same problem. After listening to music for a while(anywhere from 1 min. to many hours) the program will tell me the sound card is not configured right or is busy. The only way I have found to work around this is to restart the computer. Any advice to solve this problem?

Thanks

---

### Post by Crafty Kisses on 2007-10-29
> **LostLake said:**
> I have been experimenting with various audio players and each have the same problem. After listening to music for a while(anywhere from 1 min. to many hours) the program will tell me the sound card is not configured right or is busy. The only way I have found to work around this is to restart the computer. Any advice to solve this problem?

Thanks

Post the following output:
```
lspci
```

---

### Post by LostLake on 2007-10-30
lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
01:02.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

---

