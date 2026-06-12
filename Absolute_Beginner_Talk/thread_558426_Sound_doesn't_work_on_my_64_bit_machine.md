---
title: "Sound doesn't work on my 64 bit machine"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by tjd_maximum on 2007-09-23
Hello, I'm pretty new to Ubuntu so try to bear with me. I recently installed Ubuntu on a partition of my laptop and while I like it very much I'm having problems getting the sound to work (well, there are a few other problems but this is the major one). I've tried a few other tutorials but haven't had any luck. It seems to detect everything but there is still no sound. I also know that the speakers work because the sound works on my Windows partition. The rest of this post will be any information that I think may be relevant (or seems relevant from looking at other threads. If there is any other information you need just ask (and if possible, tell me how to get it for you). Thanks a lot.

tony@Raz:~$ sudo lshw -businfo
Password:
Bus info        Device     Class       Description
==================================================
                           system      HP Pavilion dv2000 (RV326UA#ABA)
                           bus         30B5
                           memory      BIOS
cpu@0                      processor   AMD Turion(tm) 64 X2
                           memory      L1 cache
                           memory      L2 cache
                           memory      System Memory
                           memory      SODIMM DDR Synchronous 667 MHz (1.5 ns)
                           memory      SODIMM DDR Synchronous 667 MHz (1.5 ns)
pci@00:00.0                memory      C51 Host Bridge
pci@00:00.1                memory      C51 Memory Controller 0
pci@00:00.2                memory      C51 Memory Controller 1
pci@00:00.3                memory      C51 Memory Controller 5
pci@00:00.4                memory      C51 Memory Controller 4
pci@00:00.5                memory      C51 Host Bridge
pci@00:00.6                memory      C51 Memory Controller 3
pci@00:00.7                memory      C51 Memory Controller 2
pci@00:02.0                bridge      C51 PCI Express Bridge
pci@01:00.0     eth1       network     Dell Wireless 1390 WLAN Mini-PCI Card
pci@00:03.0                bridge      C51 PCI Express Bridge
pci@00:05.0                display     C51 PCI Express Bridge
pci@00:09.0                memory      MCP51 Host Bridge
pci@00:0a.0                bridge      MCP51 LPC Bridge
pci@00:0a.1                bus         MCP51 SMBus
pci@00:0a.3                processor   MCP51 PMU
pci@00:0b.0                bus         MCP51 USB Controller
usb@1           usb1       bus         OHCI Host Controller
pci@00:0b.1                bus         MCP51 USB Controller
usb@2           usb2       bus         EHCI Host Controller
usb@2:8                    multimedia  USB 2.0 Camera
pci@00:0d.0                storage     MCP51 IDE
ide@1           ide1       bus         IDE Channel 1
ide@1.0         /dev/hdc   disk        Slimtype DVD A DS8AZH
                /dev/hdc   disk        
pci@00:0e.0     scsi0      storage     MCP51 Serial ATA Controller
scsi@0:0.0.0    /dev/sda   disk        WDC WD1200BEVS-6
scsi@0:0.0.0,1  /dev/sda1  disk        HPFS/NTFS partition
scsi@0:0.0.0,2  /dev/sda2  disk        HPFS/NTFS partition
scsi@0:0.0.0,3  /dev/sda3  disk        Linux filesystem partition
scsi@0:0.0.0,4  /dev/sda4  disk        Extended partition
                /dev/sda5  disk        Linux swap / Solaris partition
pci@00:10.0                bridge      MCP51 PCI Bridge
pci@03:09.0                bus         Ricoh Co Ltd
pci@03:09.1                system      R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
pci@03:09.2                system      Ricoh Co Ltd
pci@03:09.3                system      R5C592 Memory Stick Bus Host Adapter
pci@03:09.4                system      xD-Picture Card Controller
[COLOR="Red"]pci@00:10.1                multimedia  MCP51 High Definition Audio[/COLOR]
pci@00:14.0     eth0       bridge      MCP51 Ethernet Controller
pci@00:18.0                bridge      K8 [Athlon64/Opteron] HyperTransport Tech
pci@00:18.1                bridge      K8 [Athlon64/Opteron] Address Map
pci@00:18.2                bridge      K8 [Athlon64/Opteron] DRAM Controller
pci@00:18.3                bridge      K8 [Athlon64/Opteron] Miscellaneous Contr

---

### Post by overdrank on 2007-09-24
Hi maybe this link will help
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Good luck!

---

### Post by tjd_maximum on 2007-09-24
Thank you for the reply, I'm not sure if I should post this here or on the other thread but I'll try here first. 

> 
tony@Raz:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


And then the results of lspci -v are:

> 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
(Does that "access denied" mean anything?)

Anyway, I looked at the alsamix site and I couldn't find an exact match but I did find on (snd-hda-intel) that showed up when I hit tab after typing "modprobe snd-"). However, when I type it I get nothing back 
> 
tony@Raz:~$ sudo modprobe snd-hda-intel
tony@Raz:~$ 
Does this mean anything to anyone? Again thanks for any help.

---

