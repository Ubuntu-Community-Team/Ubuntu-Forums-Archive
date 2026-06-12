---
title: "Ethernet not working"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by g5280 on 2007-04-17
I am NEW. i haves ystem76 laptop brand new w edgy my ether net does not work when using link sys rougher or direct to switch this has been going on for 6 weeks. 76 support cant seam to help. the wirless connection is ok  could some one please point me to someone where i can pay for support or tell me where to start 
Thanks gary

---

### Post by Seisen on 2007-04-17
What is the network card you have if you don't know do this in the terminal

```
lspci
``` and post it in the thread.

---

### Post by g5280 on 2007-04-17
gary@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0398 (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
gary@ubuntu:~$ 
i hop this will help
thanks gary

---

### Post by g5280 on 2007-04-18
i am still trying to git this solves if any one could help 
Thanks gary

---

### Post by g5280 on 2007-04-18
Please disregard. The whole thing was a IP issue. Thank you any way
gary

---

