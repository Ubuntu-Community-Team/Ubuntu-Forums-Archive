---
title: "Dapper - PCMIA modem quit working"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by braddcadd on 2006-09-10
OK, I have a WINBOOK laptop with a dead (built-in) modem.  So I purchased a sportser 33.6K (US Robitics).  I had thos modem working for 1 day then I changed something and it died.  I have spent 2 days trying to get it going again, to no avail.  I am currently connected to DSL.  Can anyone help with this problem?

Output of lspci:
```

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter


```


Portion of scanModem tool (Modem.txt):
```

Modem candidates are at PCI_buses:  0000:00:02.6

Providing detail for device at PCI_bus 0000:00:02.6
  with vendor-ID:device-ID
            ----:----
Class 0703: 1039:7013   Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
  SubSystem 1019:b731   Elitegroup Computer Systems: Unknown device b731
0000:00:02.6 0703: 1039:7013 (rev a0)
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at d400 [size=256]
        I/O ports at d000 [size=128]

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 1039:7013 1019:b731 debian 2.6.15-26-386 4.0.3 4.0.3    i686


 The soft modem Subsystem operates under a controller
   1039:7013  SIS 630


```

Thanks.

---

### Post by braddcadd on 2006-09-10
Problem solved.  It seems I need to run this each time you boot the computer.
```

sudo wvdialconf

```

---

