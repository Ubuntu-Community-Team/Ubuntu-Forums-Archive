---
title: "Video Card Driver Please"
date: 2015-08-04
forum: Apple Hardware Users
---

### Post by alexander46 on 2015-08-04
Lubuntu crashes on VLC, Youtube usage.
Saw that problem in a similar topic, solved by drivers.

```
*-display
                description: VGA compatible controller
                product: RV530/M56-P [Mobility Radeon X1600]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:30 memory:80000000-87ffffff ioport:3000(size=256) memory:90300000-9030ffff memory:90320000-9033ffff

```
Can you please instruct me to solve the driver issue?


brightness to darkness drop is also a common problem on this Macbook Pro 1.1 ...

---

### Post by ajgreeny on 2015-08-04
Please do not duplicate threads about the same problem; it dilutes the community response and can be very confusing for all.

Threads merged.

I am pretty sure that the graphic card you have is only supported using the open source radeon driver.  If you have attempted to install one direct from AMD you must remove it completely and remove any **/etc/X11/xorg.conf** file that may be present, then either reboot or logout and login again to get a new xsession running.

Come back again if that is not successful and I'm sure someone will try to help.
I admit I am not aware of any specific apple hardware problems that add extra difficulties to this problem, but apple hardware is something that I do not know anything about.

---

### Post by alexander46 on 2015-08-04
Did not try anything. 
How can i update my graphic card?

---

### Post by ajgreeny on 2015-08-04
> **alexander46 said:**
> Did not try anything. 
How can i update my graphic card?
I am afraid I have no idea about that.  You do not even tell us what the machine is, only that it has that AMD card in an apple machine, and I know that apple machines do not normally update with the ease of a "normal" PC.

There is no way to update the driver from whatever you have been using and updating the hardware may be impossible, but you will need to find out about that yourself.

---

### Post by alexander46 on 2015-08-04
Macbook Pro 1.1 2006 1.83GH Intel Core Duo
lshw:
```
ab90@ab90-MacBookPro:~$ lshwWARNING: you should run this program as super-user.
ab90-macbookpro           
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1999MiB
     *-cpu
          product: Genuine Intel(R) CPU            1400  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1833MHz
          capacity: 1833MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc bts aperfmperf pni monitor vmx est tm2 xtpr pdcm dtherm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:90300000-903fffff ioport:80000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: RV530/M56-P [Mobility Radeon X1600]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:30 memory:80000000-87ffffff ioport:3000(size=256) memory:90300000-9030ffff memory:90320000-9033ffff
        *-generic UNCLAIMED
             description: Performance counters
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:90404000-90404fff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:90400000-90403fff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:90200000-902fffff ioport:90500000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 22
                serial: 00:16:cb:89:b2:c8
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.23.84 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:28 memory:90200000-90203fff ioport:2000(size=256) memory:90220000-9023ffff
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:5000(size=4096) memory:90100000-901fffff ioport:90700000(size=2097152)
           *-network
                description: Wireless interface
                product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 00:16:cb:08:ba:cd
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.19.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
                resources: irq:17 memory:90100000-9010ffff
        *-pci:3
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:1000(size=4096) memory:8c100000-900fffff ioport:88000000(size=67108864)
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:40a0(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:4080(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:4060(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:4040(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:90405400-904057ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:8c000000-8c0fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW322/323 [TrueFire] 1394a Controller
                vendor: LSI Corporation
                physical id: 3
                bus info: pci@0000:0c:03.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=248 maxlatency=24 mingnt=12
                resources: irq:19 memory:8c000000-8c000fff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:40c0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:40d8(size=8) ioport:40f4(size=4) ioport:40d0(size=8) ioport:40f0(size=4) ioport:4020(size=16) memory:90405000-904053ff
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:efa0(size=32)
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD-R   UJ-857
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: HAE4
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=open
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ab90@ab90-MacBookPro:~$ 



```

---

### Post by buzzingrobot on 2015-08-04
You can't upgrade the video card in a Macbook.

---

### Post by alexander46 on 2015-08-05
hmm think ubuntu was a bit more stable though, will go back to ubuntu then.
is there a best running linux for macbook?

---

### Post by mörgæs on 2015-08-05
Which release(s) of L/Ubuntu have you tried?

---

