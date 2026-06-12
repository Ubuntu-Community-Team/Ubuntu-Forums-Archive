---
title: "installing a driver"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by skydiver|goose on 2007-08-22
I've got this HP Pavillion ZV5000, it's a couple years old, and the Windows XP it had on it crashed (big surprise) so now I'm downloading the installer to put Ubuntu on it instead. It has an internal wifi card I want to  be able to use so that I can be counterproductive at work, but I neither know what I need to do, nor how to install it.

The only linux I've used before was Knoppix so I could recover some data on a crashed hard drive to a thumb drive, so I'm not very knowledgeable at it...

---

### Post by deadgobby on 2007-08-22
Run the CD has live and see if you get connected. So when you click on the firefox icon and get the ubuntu home. Have it go to like [http://yahoo.com](http://yahoo.com) and see if connects. If it does, you know it works right off the bat. If any other errors of running the live CD, you may need to do some mojo on getting the system to work.
Gobby

---

### Post by skydiver|goose on 2007-08-22
assuming it doesn't have the driver already, what do you mean by do some mojo?

---

### Post by deadgobby on 2007-08-22
If Ubie does not dectect the wifi card in question. You will need to debug what internal wifi card it has and grab the linux drivers to make it work. It can simple to some tinkering to get linux to use it.
Gobby

---

### Post by kevdog on 2007-08-22
look at the networking forums to get help about installing your wireless drivers.  It is a tedious process (for most), but in the end everything should work.  Hard for me to give you any advice at this point, since I know nothing about your wireless card/chipset.

---

### Post by wolfen69 on 2007-08-22
you will need to go to system>administration>network  to configure it. WEP, etc...

---

### Post by pgar23 on 2007-08-22
> **skydiver|goose said:**
> assuming it doesn't have the driver already, what do you mean by do some mojo?

He means you will probably need this program called "ndiswrapper" (you can get it from [http://www.sourceforge.net](http://www.sourceforge.net)) which allows you to use Windows drivers in Linux.
There are plenty of HOWTOs on this.

Which wifi card?

---

### Post by skydiver|goose on 2007-08-22
Well, I'm having a rather difficult time finding the actual make and model.

Like I said, it's a HP Pavillion ZV5000, and I've found a couple of specs pages on it so far like this: [http://www.research.rutgers.edu/~angheles/zv5000/hardwareSpec.html](http://www.research.rutgers.edu/~angheles/zv5000/hardwareSpec.html)

but everywhere I look I just get "integrated wireless card" or something like that. I do have the .exe installer for the wireless card drivers, though

---

### Post by skydiver|goose on 2007-08-22
on the HP website for the laptop ([http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=385148&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=385148&lang=en)) it says the driver is the " HP WLAN W400-W500 Driver for Windows 2000/XP" if that helps

---

### Post by kevdog on 2007-08-22
Type and post the following (it will give us all the information we need):

lspci -nn
lshw -C network

---

### Post by skydiver|goose on 2007-08-22
I'm assuming you  need me to type that in whatever shell command ubuntu uses. as soon as I get it up and running I'll get it for you

---

### Post by skydiver|goose on 2007-08-22
ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation nForce3 Host Bridge [10de:00d1] (rev a4)
00:01.0 ISA bridge [0601]: nVidia Corporation nForce3 LPC Bridge [10de:00d0] (rev a6)
00:01.1 SMBus [0c05]: nVidia Corporation nForce3 SMBus [10de:00d4] (rev a4)
00:02.0 USB Controller [0c03]: nVidia Corporation nForce3 USB 1.1 [10de:00d7] (rev a5)
00:02.1 USB Controller [0c03]: nVidia Corporation nForce3 USB 1.1 [10de:00d7] (rev a5)
00:02.2 USB Controller [0c03]: nVidia Corporation nForce3 USB 2.0 [10de:00d8] (rev a2)
00:06.0 Multimedia audio controller [0401]: nVidia Corporation nForce3 Audio [10de:00da] (rev a2)
00:06.1 Modem [0703]: nVidia Corporation nForce3 Audio [10de:00d9] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation nForce3 IDE [10de:00d5] (rev a5)
00:0a.0 PCI bridge [0604]: nVidia Corporation nForce3 PCI Bridge [10de:00dd] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation nForce3 AGP Bridge [10de:00d2] (rev a4)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 420 Go 32M] [10de:0176] (rev a3)
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
02:04.0 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.1 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.2 System peripheral [0880]: Texas Instruments PCI1620 Firmware Loading Function [104c:8201] (rev 01)
ubuntu@ubuntu:~$ lshw -c network
Hardware Lister (lshw) - B.02.08.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.08.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

---

### Post by Viruss on 2007-08-22
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SB600 SMBus [1002:4385] (rev 13)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SB600 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SB600 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 01)
viruss@viruss-laptop:~$ lshw -C
Hardware Lister (lshw) - B.02.08.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.08.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

viruss@viruss-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:92:ee:80:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=0 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0200000-c0203fff irq:19
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:67:b2:c4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.0.100 latency=64 multicast=yes
       resources: iomemory:c0300000-c0301fff irq:21
viruss@viruss-laptop:~$ sudo lshw -C network
Password:
  *-network DISABLED      
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:92:ee:80:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0200000-c0203fff irq:19
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:67:b2:c4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.0.100 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:c0300000-c0301fff irq:21

---

