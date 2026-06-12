---
title: "New sata drive not recognized"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by mathemagician on 2008-01-20
I just bought a new 320g Seagate internal SATA drive to use as a secondary drive on my Kubuntu 7.10 system (80g IDE system drive).

The SATA drive is recognized in BIOS, but not in Kubuntu. QTParted shows only my system drive.

Any suggestions?

---

### Post by blueridgedog on 2008-01-20
Do you have any SATA devices recognized by Ubuntu?

does 

```
lspci
```

Show your SATA controller?  

Here is mine:
```

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
```

Is the disk/controller shown in the output of
```

lshw 
```

---

### Post by mathemagician on 2008-01-20
It looks like lspci shows my sata controller. Here's the output.

```
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 0
2)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02
)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memor
y Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr                                                                                oller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Cont                                                                                roller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Brid                                                                                ge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller                                                                                 (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 0                                                                                2)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 A-LE (rev a1)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (                                                                                rev 80)
02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell]                                                                                 (rev 12)
02:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (                                                                                rev 46)
02:0c.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multipro                                                                                tocol MAC/baseband processor (rev 01)
02:0d.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI                                                                                 Multi-Channel I/O Controller (rev 02)

```

I'm not sure what to look for in the lshw output, so here it is:

```
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
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
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 82875P/E7210 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=i82875p_edac module=i82875p_edac
        *-pci:0
             description: PCI bridge
             product: 82875P Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: GeForce 6200 A-LE
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-system UNCLAIMED
             description: System peripheral
             product: 82875P/E7210 Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire:0
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
           *-network:0
                description: Ethernet interface
                product: 3c940 10/100/1000Base-T [Marvell]
                vendor: 3Com Corporation
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 12
                serial: 00:0c:6e:39:ef:72
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=skge driverversion=1.11 firmware=N/A latency=64 maxlatency=31 mingnt=23 module=skge multicast=yes
           *-firewire:1
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 46
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
           *-network:1
                description: Wireless interface
                product: AR5212/AR5213 Multiprotocol MAC/baseband processor
                vendor: Atheros Communications, Inc.
                physical id: c
                bus info: pci@0000:02:0c.0
                logical name: wifi0
                version: 01
                serial: 00:0f:3d:ab:fa:ee
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.1.34 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
           *-multimedia
                description: Multimedia audio controller
                product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
                vendor: VIA Technologies Inc.
                physical id: d
                bus info: pci@0000:02:0d.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ICE1712 latency=64 module=snd_ice1712
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

---

### Post by mathemagician on 2008-01-20
I'd also like to note that since installing the SATA drive in my system, Kubuntu takes considerably longer to boot. 

It seems to hang at Kubuntu splash screen for a minute or two before proceeding with the boot sequence. Is there a way I can see what procedure(s) that it's hanging on?

---

### Post by blueridgedog on 2008-01-20
Well, it sees your controller:

```
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
```

Just to be certain that is doesn't see the drive, can you post the output of:

```
sudo fdisk -lu
```

Some things to check:

-it is plugged in to an SATA port and not an onboard RAID port
-it has power and the data cable is securely pushed in.

There is a remote chance that the drive is DOA, but given that that is remote, lets keep looking.

---

### Post by mathemagician on 2008-01-20
I verified that the drive is indeed connected to a SATA port and not a RAID port, and I checked all the connections. And like I said, the drive is being recognized by BIOS but seems to be causing a serious slowdown of my Kubuntu bootup time. The progress bar is stuck at the top for a good 2-3 minutes longer than it did before I hooked up the drive.

Here is the output of "sudo fdisk -lu"

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf061f061

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   153276164    76638051   83  Linux
/dev/sda2       153276165   156296384     1510110    5  Extended
/dev/sda5       153276228   156296384     1510078+  82  Linux swap / Solaris

```

---

### Post by blueridgedog on 2008-01-20
Well, my only guess is that it is a new drive (SATA II) plugged in to an SATA 150 controller.  They are typically backwards compatible, but you never know.  There is usually a jumper on the drive to force SATA 150 compatibility.  If you think this is remotely on track, you might want to try setting it.  Otherwise, I am stumped at the moment.

---

### Post by mathemagician on 2008-01-21
I'll take a look when I get home, but I'm pretty sure the jumper was set that way from factory. Hopefully, I'm wrong and the jumper setting will fix it.

---

