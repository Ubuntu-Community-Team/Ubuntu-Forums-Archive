---
title: "Ethernet as bridge?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Silent Warrior on 2006-08-06
I said I'd be back, didn't I? It's a whole bunch of hardware/driver-problems I have with me today, but since I've had Linux installed a whopping 2-3 days, I hope I still qualify as an Absolute Beginner.
Appetizer: My Linux-system (Ubuntu 6.06) is a different machine altogether from this WinXP-machine I'm using right now (my mother's). No internet in Linux (one of the issues), working just fine in XP.

Issue #1: My ethernet-controller claims to be a bridge?!
I've scoured the forums and found this guide: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
Although my connection is wired (but to a wireless router), it didn't seem like such a bad place to start. I can ping 127.0.0.1 alright, but I can't seem to reach the router.
One of the first steps is fiddling about with lshw and lspci. Sure. I see I have a NVidia Corp. MCP55 Ethernet-controller (WTF? ASUS said it was a Gigabit LAN-thing!), classed as bridge. And device eth0. The guide suggests that should read class: network, not bridge. Is that a problem? How do I make it go away if it is?

Issue #2: Driver-installation 1
I have a flashy little Radeon X1900XT strapped into my PCI-E-slot, and I'm getting a bit tired of 1024x768 (the letters look so huge!). So, I'd like to install those new 8.27-drivers, I was hoping to play some games on that rig, no go without drivers. It's just that every time I've tried, xorg.conf was buggered up and Ubuntu booted in commandline-interface only. Since I have no idea how to recover from that in an orderly fashion, I've simply reinstalled Ubuntu every time it's happened. Naturally, I don't want it to happen again if it can be avoided. Alright then, how DO I install it without messing up X-org? I've seen some manner of guides around the Hardware-support forums, but I haven't dared try any of them yet. There are two additional downloads, not just the driver-package, available from ATI, should I get one or both of them?

Issue #3: Driver-installation 2
I have a Promise RAID-controller (suffice it to say I made an uninformed purchase and had developed a real liking to the stuff on my IDE-drives - my ASUS M2N-E expected its users to have SATA-HDs), and it's detected as an IDE-controller. This is quite secondary because that other HD uses NTFS, and I have quite enough space on the main HD for now. I hear NTFS-support in Linux isn't quite stellar, correct? I don't want to lose that data, and I can always improvise something by WinRAR and the Windows-machine.
All that aside, I want to make this work. The drivers I downloaded from Promise's site claimed there was no supported hardware attached. I swear I downloaded the correct .zip, and STILL...
Should I keep trying with this controller, or should I use a IDE->USB-adapter instead? I'm leaning towards the latter, since one PCI-slot doesn't seem to be healthy, making 'em a scarce commodity. As long as I get by without a not-onboard network-card, it shouldn't be a problem in that regard, however.

Issue #4: Linux and X-Fi
I understand there's no official driver-support for this combination until next year, correct? Now, until I start getting things set up and working (and WineX or Cedega) this won't really matter, as the onboard sound is sufficient for playing CDs. An ICQ-mate and fellow Ubuntu-user said the X-Fi would work in Ubuntu if I poked around with the volume-control. What's the score here? Also, that wire going from the CD to the CD-Audio connector on the soundcard (and likely somewhere on the mobo?), isn't that supposed to be mandatory for playing CDs? Well, I don't have it attached and I hear the music just fine. Wazzup?

Issue #5: ... I need a great big tome o' Ubuntu terminal-commands with cross-indexing... Blargh...

---

### Post by pdub on 2006-08-06
Issue #1:

Please post the results from lspci and lshw along with /etc/network/interfaces.

Issue #2:

Please see the following How-To for installing ATI drivers. This is an excellent overall guide for configuring Ubuntu.

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Issue #3:

I have a promise RAID controller on my ASUS motherboard and an additional Promise PCI SATA RAID controller. I gave up trying to make either card work properly.

Issue #4:

I have no idea.

---

### Post by Silent Warrior on 2006-08-06
1#: lspci:
0000:00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
0000:00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
0000:00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
0000:00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
0000:00:06.0 PCI bridge: nVidia Corporation: Unknown device 0370 (rev a2)
0000:00:06.1 0403: nVidia Corporation: Unknown device 0371 (rev a2)
0000:00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
0000:00:0a.0 PCI bridge: nVidia Corporation: Unknown device 0376 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 0374 (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 0374 (rev a2)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 0378 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 0375 (rev a2)
0000:00:0f.0 PCI bridge: nVidia Corporation: Unknown device 0377 (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:07.0 RAID bus controller: Promise Technology, Inc. PDC20270 (FastTrak100 LP/TX2/TX4) (rev 02)
0000:07:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7249
0000:07:00.1 Display controller: ATI Technologies Inc: Unknown device 7269

lshw:
***
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1022MB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy cpufreq
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.1515ns)
          capabilities: bus_master cap_list
     *-isa UNCLAIMED
          description: ISA bridge
          product: MCP55 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
     *-serial UNCLAIMED
          description: SMBus
          product: MCP55 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          resources: ioport:1c00-1c3f ioport:1c40-1c7f irq:255
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-usb:0
          description: USB Controller
          product: MCP55 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd
          resources: iomemory:fe02f000-fe02ffff irq:58
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.15-23-amd64-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=10 speed=12.0MB/s
           *-usb
                description: Mouse
                product: Microsoft USB Wireless Mouse
                vendor: Microsoft
                physical id: 4
                bus info: usb@2:4
                version: 0.17
                capabilities: usb-2.00
                configuration: driver=usbhid maxpower=50mA speed=1.5MB/s
     *-usb:1
          description: USB Controller
          product: MCP55 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd
          resources: iomemory:fe02e000-fe02e0ff irq:50
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.15-23-amd64-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=10 speed=480.0MB/s
           *-usb
                description: Mass storage device
                product: Flash Disk
                vendor: USB
                physical id: 1
                bus info: usb@1:1
                version: 2.00
                serial: 61100741A93F18DE
                capabilities: usb-2.00 scsi
                configuration: driver=usb-storage maxpower=200mA speed=480.0MB/s     *-ide
          description: IDE interface
          product: MCP55 IDE
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE
          resources: ioport:f400-f40f
        *-ide
             description: IDE Channel 0
             physical id: 0
             bus info: ide@0
             logical name: ide0
             clock: 66MHz
           *-disk
                product: WDC WD800BB-00JHC0
                vendor: Western Digital
                physical id: 0
                bus info: ide@0.0
                logical name: /dev/hda
                capacity: 74GB
           *-cdrom
                product: _NEC DVD_RW ND-1300A
                physical id: 1
                bus info: ide@0.1
                logical name: /dev/hdb
                capabilities: packet
     *-pci:0
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
        *-storage
             description: RAID bus controller
             product: PDC20270 (FastTrak100 LP/TX2/TX4)
             vendor: Promise Technology, Inc.
             physical id: 7
             bus info: pci@01:07.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=Promise_IDE
             resources: ioport:ec00-ec07 ioport:e800-e803 ioport:e400-e407 ioport:e000-e003 ioport:dc00-dc0f iomemory:fdef0000-fdefffff irq:233
     *-multimedia
          description: Multimedia controller
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 6.1
          bus info: pci@00:06.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel
          resources: iomemory:fe024000-fe027fff irq:74
     *-bridge
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@00:08.0
          logical name: eth0
          version: a2
          serial: 00:17:31:d9:ba:bf
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth multicast=yes
          resources: iomemory:fe02d000-fe02dfff ioport:f000-f007 iomemory:fe02c000-fe02c0ff iomemory:fe02b000-fe02b00f irq:66
     *-pci:1
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@00:0a.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:5
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@00:0e.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:6
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@00:0f.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display:0
             description: VGA compatible controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 0
             bus info: pci@07:00.0
             version: 00
             size: 256MB
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:e0000000-efffffff iomemory:fddf0000-fddfffff ioport:cc00-ccff irq:10
        *-display:1 UNCLAIMED
             description: Display controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 0.1
             bus info: pci@07:00.1
             version: 00
             size: 64KB
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:fdde0000-fddeffff
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
  *-scsi
       physical id: 1
       bus info: scsi@0
       logical name: scsi0
       capabilities: scsi-host
       configuration: driver=usb-storage
(That last entry is the USB-stick I used for saving the raw text-output on, so I wouldn't have to run back and forth, typing by memory. It isn't a constant resident.)

cat /etc/network/interfaces:
auto lo
iface lo inet loopback

iface eth0 inet dhcp
network 213.66.186.0
broadcast 213.66.186.255
auto eth0

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider

#2: Still nervous... but it's worth a try. I'll do that once I get internet going.

#3: Right... If no-one says anything to the contrary during next week, that controller goes right back to the store. pci_available+=1.

#5: I'll just fire up OpenOffice and make one, why don't I? Go all-encompassing open-source-software-bundles!

[GRAND UPDATE]
Never you mind about #1. I just plugged in that other network-card I have, a ZEN3200W, and I can connect just fine. WHEEE! So now I guess the only issues FOR NOW are 3-5. Let's see some action about the Promise-gear, gents! (Even if it is a non-budging "recommendation" to use USB->IDE-adapters.)

---

