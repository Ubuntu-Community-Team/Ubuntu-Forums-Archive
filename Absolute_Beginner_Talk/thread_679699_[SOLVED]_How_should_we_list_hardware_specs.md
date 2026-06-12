---
title: "[SOLVED] How should we list hardware specs"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Motorhead Kaze on 2008-01-27
Often when I have questions about my innumerable problems I am asked to post hardware specs.  Even after using Ubuntu all year as my only OS, I'm still a noob.  A lot of frequent fliers on the forum just have the basics in their signatures, this seems like a good idea.  Questions:

1.  I know that processor, RAM and graphics card info is needed.  What else do people who are answering posts want to know?

2.  I have looked in system/preferences/hardware info, also at system/administration/system monitor and sudo lshw in the terminal and I see it all there, but not sure what I should be paying attention to.

So far, I see I have an AMD Sempron processor 3400+, 2GHz, 64 bits and under "K8"  I see Anthlon 64/Opteron.  I see on the AMD website these are 3 different processors, and all names appear under my device manager.  How do I understand which I have, or rather, how do I list this info?

Vid card:  nVidia C51G [GeForce 6100]  how should this be listed? Without the C51G part or with?

Thanks!

---

### Post by Ub1476 on 2008-01-27
Video card, sound card and wireless card are important. It's also good to know wether you are running Ubuntu 32-bit or 64-bit. You can get a complete list by typing:

```
lspci
```

Motherboard and such isn't really important. Maybe if you have problems starting the live cd, but anything else, no..

You should list the complete sentence the lspci command give for your say, VGA controller (video card). It makes it easier to troubleshoot.

---

### Post by amo-ej1 on 2008-01-27
Well it mainly depends what your problems is about. 

-> If the problems concerns 32bit vs 64 it is sufficient to know what cpu you use (a slow pentium is no different from a fast pentium) (info contained in cat /proc/cpuinfo)

-> if the problem is storage related, it is usefull to know which disks you have, how they are configured (man mount) , and how they are connected and how they are mounted (man mount)

-> If the problem is related to some pci add-in card it is best to say which card it is, man lspci (type lspci -v)

-> if it is related to some usb device, (man lsusb) 

.... 

when in doubt, try to be as complete as possible, or it will be the first question to receive back instead of a solution ;)

---

### Post by Dr Small on 2008-01-27
Hi, why don't you install System Info? It lists most of the highly important stuff right inside of it :D

```
sudo apt-get install sysinfo
```

---

### Post by Lord Illidan on 2008-01-27
For more info on the cpu, you can also use

```
cat /proc/cpuinfo
```

---

### Post by John.Michael.Kane on 2008-01-27
You can also pass the command below

 ```
lshw -short
```

Example output listed below.
```
H/W path           Device      Class       Description
======================================================
                               system      P35-DS3L
/0                             bus         P35-DS3L
/0/0                           memory      128KiB BIOS
/0/4                           processor   Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz
/0/4/a                         memory      64KiB L1 cache
/0/4/b                         memory      1MiB L2 cache
/0/1b                          memory      2GiB System Memory
/0/1b/0                        memory      DIMM [empty]
/0/1b/1                        memory      1GiB DIMM 800 MHz (1.2 ns)
/0/1b/2                        memory      DIMM [empty]
/0/1b/3                        memory      1GiB DIMM 800 MHz (1.2 ns)
/0/100                         bridge      82G33/G31/P35/P31 Express DRAM Controller
/0/100/1                       bridge      82G33/G31/P35/P31 Express PCI Express Root Port
/0/100/1/0                     display     G71 [GeForce 7900 GTX]
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a/1        usb3        bus         UHCI Host Controller
/0/100/1a/1/1                  generic     USB Keyboard
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.1/1      usb4        bus         UHCI Host Controller
/0/100/1a.1/1/1                generic     USB Receiver
/0/100/1a.2                    bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1a.2/1      usb5        bus         UHCI Host Controller
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1a.7/1      usb1        bus         EHCI Host Controller
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1c                      bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1c.3                    bridge      82801I (ICH9 Family) PCI Express Port 4
/0/100/1c.3/0                  storage     JMB368 IDE controller
/0/100/1c.4                    bridge      82801I (ICH9 Family) PCI Express Port 5
/0/100/1c.4/0      eth0        network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d/1        usb6        bus         UHCI Host Controller
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.1/1      usb7        bus         UHCI Host Controller
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.2/1      usb8        bus         UHCI Host Controller
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1d.7/1      usb2        bus         EHCI Host Controller
/0/100/1e                      bridge      82801 PCI Bridge
/0/100/1f                      bridge      82801IB (ICH9) LPC Interface Controller
/0/100/1f.2        scsi0       storage     82801IB (ICH9) 4 port SATA AHCI Controller
/0/100/1f.2/0      /dev/cdrom  disk        DVDRW LH-20A1L
/0/100/1f.2/0/0    /dev/cdrom  disk        
/0/100/1f.2/1      /dev/sda    disk        80GB WDC WD800JD-00LS
/0/100/1f.2/1/1    /dev/sda1   volume      196MiB EXT3 volume
/0/100/1f.2/1/2    /dev/sda2   volume      74GiB Linux LVM Physical Volume partition
/0/100/1f.2/0.0.0  /dev/sdb    disk        251GB WDC WD2500YS-01S
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
```

Should you want to give more detail pass the below command.

```
 lspci -v
``` (note if lspci -v does not give enough info you can pass the -vv or -vvv option)

Example output listed below.
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5000
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information <?>

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f4000000-f6ffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: [88] Subsystem: Giga-byte Technology Unknown device 5000
        Capabilities: [80] Power Management version 3
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [a0] Express Root Port (Slot+), MSI 00
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e100 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at e200 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e000 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at fa004000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device a002
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fa000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Giga-byte Technology Unknown device 5001
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f7000000-f7ffffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Giga-byte Technology Unknown device 5001
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: 0000000080000000-00000000800fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Giga-byte Technology Unknown device 5001
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at e300 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at e400 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e500 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at fa005000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Capabilities: [50] Subsystem: Giga-byte Technology Unknown device 5000

00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information <?>
        Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801IB (ICH9) 4 port SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Giga-byte Technology Unknown device b005
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2299
        I/O ports at e600 [size=8]
        I/O ports at e700 [size=4]
        I/O ports at e800 [size=8]
        I/O ports at e900 [size=4]
        I/O ports at ea00 [size=32]
        Memory at fa006000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] SATA HBA <?>
        Capabilities: [b0] PCIe advanced features <?>
        Kernel driver in use: ahci
        Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: medium devsel, IRQ 18
        Memory at fa007000 (64-bit, non-prefetchable) [size=256]
        I/O ports at 0500 [size=32]
        Kernel driver in use: i801_smbus
        Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GTX] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: nVidia Corporation Unknown device 040d
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f5000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at b000 [size=128]
        [virtual] Expansion ROM at f6000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint, MSI 00
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nvidia

03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Unknown device b000
        Flags: bus master, fast devsel, latency 0, IRQ 19
        I/O ports at c000 [size=8]
        I/O ports at c100 [size=4]
        I/O ports at c200 [size=8]
        I/O ports at c300 [size=4]
        I/O ports at c400 [size=16]
        Capabilities: [68] Power Management version 2
        Capabilities: [50] Express Legacy Endpoint, MSI 01
        Kernel driver in use: pata_jmicron
        Kernel modules: pata_jmicron, ata_generic

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Giga-byte Technology Unknown device e000
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at d000 [size=256]
        Memory at f9000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data <?>
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint, MSI 00
        Capabilities: [84] Vendor Specific Information <?>
        Kernel driver in use: r8169
        Kernel modules: r8169
```

Also make sure to wrap your text using the code tag feature.

---

### Post by Motorhead Kaze on 2008-01-27
Holy cow.  I tried all.  (I was looking for that lshw -short command today)

 Next time someone asks, I'll know what to list.  Thanks a lot.

---

### Post by John.Michael.Kane on 2008-01-27
> **Motorhead Kaze said:**
> Holy cow.  I tried all.  (I was looking for that lshw -short command today)

 Next time someone asks, I'll know what to list.  Thanks a lot.

Your welcome. I am glad the information helped.

---

### Post by Motorhead Kaze on 2008-01-27
Just a test of my understanding or lack of it:
The following list tells me I have a AMD Sempron Processor or should I call it an AMD Sempron K8 Processor?  Since I see a lot of 64's down there (/0/100 bridge K8 [Athlon64/Opteron] HyperTransport Technology) and Sepmpron models these days are "64 Semprons" can I conclude with some certainty that I'm using what we'd call a 64bit processor?  Does that mean that the next time I install Ubuntu, I should be using 64 bit version?  

Funny/odd/typical?, when I click on nVidia in "Sysinfo" sysinfo crashes.  Oh I see, nVidia means "Shut down".  Hmmm.

I appreciate your help.  Trying to graduate from "Noob" takes time.

H/W path Device Class Description
===========================================
system Computer
/0 bus Motherboard
/0/1 memory 894MB System memory
/0/6 processor AMD Sempron(tm) Processor 3400+
/0/6/0 memory 128KB L1 cache
/0/6/1 memory 256KB L2 cache
/0/0 memory RAM memory
/0/0.1 memory RAM memory
/0/0.2 memory RAM memory
/0/0.3 memory RAM memory
/0/0.4 memory RAM memory
/0/0.5 memory RAM memory
/0/0.6 memory RAM memory
/0/0.7 memory RAM memory
/0/2 bridge C51 PCI Express Bridge
/0/3 bridge C51 PCI Express Bridge
/0/4 bridge C51 PCI Express Bridge
/0/5 display C51G [GeForce 6100]
/0/9 memory RAM memory
/0/a bridge MCP51 LPC Bridge
/0/a.1 bus MCP51 SMBus
/0/a.2 memory RAM memory
/0/b bus MCP51 USB Controller
/0/b.1 bus MCP51 USB Controller
/0/d storage MCP51 IDE
/0/d/0 ide0 bus IDE Channel 0
/0/d/0/0 /dev/hda disk 298GB ST3320620A
/0/d/1 ide1 bus IDE Channel 1
/0/d/1/0 /dev/hdc disk DVD DC DW1670
/0/e storage MCP51 Serial ATA Controller
/0/10 bridge MCP51 PCI Bridge
/0/10.2 multimedia MCP51 AC97 Audio Controller
/0/14 eth0 bridge MCP51 Ethernet Controller
/0/100 bridge K8 [Athlon64/Opteron] HyperTransport Technology
/0/101 bridge K8 [Athlon64/Opteron] Address Map
/0/102 bridge K8 [Athlon64/Opteron] DRAM Controller
/0/103 bridge K8 [Athlon64/Opteron] Miscellaneous Control
/1 scsi2 storage

---

