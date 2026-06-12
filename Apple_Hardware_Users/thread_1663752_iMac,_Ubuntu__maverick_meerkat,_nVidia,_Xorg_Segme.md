---
title: "iMac, Ubuntu  maverick meerkat, nVidia, Xorg Segmentation fault"
date: 2011-01-10
forum: Apple Hardware Users
---

### Post by azeemarif on 2011-01-10
Hello,

I recently received an old iMac from my brother.
It is a late 2006, 24 inch intel core2duo white imac.
The DVD super driver does not work and HDD was wiped clean.

So when I received it, there was no Mac OS on this machine (actually there was no OS at all) and also I did not have access to original Mac OS install DVD.

I managed to install Ubuntu 10.10 on it and I am able to boot into Ubuntu using rEFIt and grub2 EFI (the so called pure EFI boot).

The machine has a nVidia GeForce 7300GT GPU. But I am able to boot this iMac in graphics mode only is I provide boot parameter video=efifb and use "fbdev" driver in xorg.conf.

If I enable nVidia driver, Xorg crashes with the following message
```
(II) May 04 19:07:13 NVIDIA(0): Setting mode "nvidia-auto-select"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x675410]
Segmentation fault at address 0x24

Caught signal 11 (Segmentation fault). Server aborting
```

  

dmidecode output:
```
BIOS Information
       Vendor: Apple Computer, Inc.
       Version:     IM61.88Z.0093.B07.0706281250
       Release Date: 06/28/07
       ROM Size: 2048 kB
       Characteristics:
               PCI is supported
               BIOS is upgradeable
               BIOS shadowing is allowed
               Boot from CD is supported
               Selectable boot is supported
               ACPI is supported
               IEEE 1394 boot is supported
               Smart battery is supported
               Function key-initiated network boot is supported
       BIOS Revision: 0.1

Handle 0x0001, DMI type 1, 27 bytes
System Information
       Manufacturer: Apple Computer, Inc.
       Product Name: iMac6,1
       Version: 1.0
```

lspci output:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 01)
04:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
```



Any idea if there is a way to enable nVidia driver on this machine without crashing Xorg?

Thanks
azeemarif

---

### Post by azeemarif on 2011-01-11
Found another thread with similar problem but with no answers :(
[http://ubuntuforums.org/showthread.php?t=1473775]("http://ubuntuforums.org/showthread.php?t=1473775")

Any suggestion? 

Thanks

---

