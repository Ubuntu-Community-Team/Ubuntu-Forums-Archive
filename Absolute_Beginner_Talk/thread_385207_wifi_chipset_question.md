---
title: "wifi chipset question"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2007-03-15
hey guys quick question. im trying to set up my wifi on my hp pavilion dv6000 but i need my network drivers. how can i tell wich drivers and chipset i need?

lspci:

mike@mike-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
05:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)

---

### Post by lamalex on 2007-03-15
You have a broadcom 4311. this one is quite easy to set up (at least i've had very good luck)

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by da1nonlymikeo on 2007-03-15
i followed all the steps in that link and now i do have the network maneger in my top right screen but when i right click/properties there is no eth1. just eth0 and lo. and when i manually type in eth1 the signal strength comes up as zero.

my card is working tho becuase when i start wifi radar it finds my network. i just cant connect to it for some reason??

can anyone help?

---

