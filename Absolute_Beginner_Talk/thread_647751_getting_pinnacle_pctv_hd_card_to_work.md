---
title: "getting pinnacle pctv hd card to work"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-12-22
Greetings all,
Today was an early christmas for me, and my family got a pinnacle pctv hd card for me, but I have no idea how to get it running under ubuntu.  I am still pretty clueless about making drivers and stuff like that.  Any help would begreatly appreciated.
Thanks

---

### Post by jken146 on 2007-12-22
First step:  stick the card in, boot up Ubuntu, and type ```
lspci
``` to see if it's recognised.  ```
lshw
``` may give you more details too.

After that, see if you can watch TV (there are a few apps out there for this, e.g. myth tv).  If not, do some searching and post back if you still need help.

---

### Post by mangurt on 2007-12-22
Great! Thanks for the response.  Gotta wait for the children to get off my computer (watching a movie right now), but I will post if it does not work.
Thanks

---

### Post by Zenthes on 2007-12-22
What no dual monitors?! man get that tuner card working and hook a darn TV up to it!!

but yeah i was looking at mythtv sounds exactily like what you need.
If you can't get it working right try poking into mediabuntu's forums they'd be able to help you with support much more.

---

### Post by mangurt on 2007-12-23
Ok,
This is what I got from the lspci command

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0c.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0c.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
00:0c.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

And this from the lshw command

 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1011MB
     *-cpu
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.4.10
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up ts fid vid ttp
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MB
     *-pci:0
          description: Host bridge
          product: VT8385 [K8T800 AGP] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=8 module=amd64_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI bridge [K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RV280 [Radeon 9200 PRO]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32 mingnt=8
        *-multimedia:0
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
        *-input
             description: Input device controller
             product: SB Live! Game Port
             vendor: Creative Labs
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp
        *-multimedia:1
             description: Multimedia video controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder
             vendor: Conexant
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20 module=cx8800
        *-multimedia:2
             description: Multimedia controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
             vendor: Conexant
             physical id: c.1
             bus info: pci@0000:00:0c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=cx88_audio latency=32 maxlatency=255 mingnt=4 module=cx88_alsa
        *-multimedia:3 UNCLAIMED
             description: Multimedia controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
             vendor: Conexant
             physical id: c.2
             bus info: pci@0000:00:0c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32 maxlatency=88 mingnt=6
        *-firewire
             description: FireWire (IEEE 1394)
             product: IEEE 1394 Host Controller
             vendor: VIA Technologies, Inc.
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
        *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list
             configuration: driver=sata_via latency=32 module=sata_via
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: SONY DVD RW DW-U18A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 13
             bus info: pci@0000:00:13.0
             logical name: eth0
             version: 10
             serial: 00:40:ca:75:c8:97
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.47 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage

I am guessing that ubuntu sees the card, but I still can't get myth tv to see it.

Any ideas?

Thanks

---

### Post by mangurt on 2007-12-24
Ok, I've been searching around the net about this card, and it looks as of 2 months ago that mythtv did not support this card.  Joy oh joy....

Even though mythtv does not support this card, would I still be able to use VLC or kaffene to watch TV?  Is there any way to get this card working through ubuntu?

Thanks again..

---

