---
title: "Wireless Card or something"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Cyprian on 2007-10-02
I have zero knowledge of Ubuntu and barely much more about computers. I can't seem to access wireless internet and I tried following the directions in the help place but since I don't know what my wireless card is I don't think it can help me much. My laptop is new and I got pissed off at vista so I got this. 
The only things I see about my wireless(on the stickers still there) is : 802.11b/g wireless LAN and Acer SignalUp: High efficiency antenna technology.
And I don't know if this has anything to do with it but it says "mobile" so ...here: AMD Turion 64 Mobile Technology.
I doubt anything I said will be of mush use but any help will be appreciated.

---

### Post by Lambert on 2007-10-02
Definitely need to find out more about what card/chipset is in your laptop.

You said you're new so if something doesn't make sense, ask for clarification.

Under applications there is a program called terminal. Open this up and type the following command.

```

sudo lshw

```

It will ask you for your administrator (root) password you set up when you installed.

It will post some information, scan through this and post here anything that looks like it's a network card. Should be 10-15 lines of information. This command shows all hardware on your pc and information about each device.

If you can't figure it out, post all the otuput and someone here can scan through it and find what they need to take the next step.

If you need, look through more posts by me. I just posted an example recently of what the output should look like that is needed.

---

### Post by cmnorton on 2007-10-02
You will need the username and password of the person who installed the computer. Is your wireless network password protected?

Which version of Ubuntu did you install? If you installed 7.04, you're likely to see the Network Manager Applet sitting on the top menu probably to the far right. You should be able to select the wireless network you want to use, and configure from there.

If prompted for a password, use the administrator's password (probably yours). 

Basically, you want to enter a passphrase if your router uses one -- eventually it should to keep your network available to you.  You'll have to play around with this, but you want to make sure wireless networking is enabled (check mark) and you set it up, probably DHCP so you can get connectivity.

---

### Post by Cyprian on 2007-10-02
Yeah....um... I gots junk loads of info, and I found a few things that MIGHT be it but I don't know. So heres all the info:

    description: Notebook 
    product: Aspire 5100 
    vendor: Acer 
    version: V2.83 
    serial: LXAX90X050714084371601 
    width: 32 bits 
    capabilities: smbios-2.4 dmi-2.4 
    configuration: boot=normal chassis=notebook uuid=620C6775-22DE-6E83-3995-0016D4D3044D 
  *-core 
       description: Motherboard 
       product: Navarro 
       vendor: Acer 
       physical id: 0 
       version: N/A 
       serial: LXAX90X050714084371601 
     *-firmware 
          description: BIOS 
          vendor: Acer 
          physical id: 0 
          version: V2.83 (03/21/2007) 
          size: 109KB 
          capacity: 960KB 
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification 
     *-cpu 
          description: CPU 
          product: AMD Turion(tm) 64 Mobile Technology MK-38 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 4 
          bus info: cpu@0 
          version: 15.12.2 
          slot: Socket M2/S1G1 
          size: 800MHz 
          capacity: 2200MHz 
          width: 64 bits 
          clock: 200MHz 
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni cx16 lahf_lm svm cr8legacy ts fid vid ttp tm stc cpufreq 
        *-cache:0 
             description: L2 cache 
             physical id: 5 
             slot: L2 Cache 
             size: 512KB 
             capacity: 1MB 
             capabilities: synchronous internal write-back 
        *-cache:1 
             description: L1 cache 
             physical id: 0 
             size: 128KB 
        *-cache:2 
             description: L2 cache 
             physical id: 1 
             size: 512KB 
     *-memory 
          description: System Memory 
          physical id: a 
          slot: System board or motherboard 
          size: 1GB 
        *-bank:0 
             description: DIMM Synchronous 
             physical id: 0 
             slot: S1 
             size: 512MB 
             width: 64 bits 
        *-bank:1 
             description: DIMM Synchronous 
             physical id: 1 
             slot: S2 
             size: 512MB 
             width: 64 bits 
     *-pci:0 
          description: Host bridge 
          product: RS480 Host Bridge 
          vendor: ATI Technologies Inc 
          physical id: 100 
          bus info: pci@00:00.0 
          version: 10 
          width: 32 bits 
          clock: 66MHz 
          configuration: latency=64 
        *-pci:0 
             description: PCI bridge 
             product: RS480 PCI Bridge 
             vendor: ATI Technologies Inc 
             physical id: 1 
             bus info: pci@00:01.0 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: pci normal_decode bus_master cap_list 
           *-display 
                description: VGA compatible controller 
                product: RS482 [Radeon Xpress 200M] 
                vendor: ATI Technologies Inc 
                physical id: 5 
                bus info: pci@01:05.0 
                version: 00 
                size: 256MB 
                width: 32 bits 
                clock: 66MHz 
                capabilities: vga bus_master cap_list 
                configuration: latency=66 mingnt=8 
                resources: iomemory:c0000000-cfffffff ioport:9000-90ff iomemory:b0100000-b010ffff irq:11 
        *-pci:1 
             description: PCI bridge 
             product: RS480 PCI Bridge 
             vendor: ATI Technologies Inc 
             physical id: 4 
             bus info: pci@00:04.0 
             version: 00 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci normal_decode bus_master cap_list 
             configuration: driver=pcieport-driver 
           *-network UNCLAIMED 
                description: Ethernet controller 
                product: Atheros Communications, Inc. 
                vendor: Atheros Communications, Inc. 
                physical id: 0 
                bus info: pci@02:00.0 
                version: 01 
                width: 64 bits 
                clock: 33MHz 
                capabilities: cap_list 
                configuration: latency=0 
                resources: iomemory:54000000-5400ffff irq:19 
        *-pci:2 
             description: PCI bridge 
             product: ATI Technologies Inc 
             vendor: ATI Technologies Inc 
             physical id: 5 
             bus info: pci@00:05.0 
             version: 00 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci normal_decode bus_master cap_list 
             configuration: driver=pcieport-driver 
        *-ide:0 
             description: IDE interface 
             product: ATI 4379 Serial ATA Controller 
             vendor: ATI Technologies Inc 
             physical id: 12 
             bus info: pci@00:12.0 
             logical name: scsi0 
             logical name: scsi1 
             version: 80 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ide bus_master cap_list emulated scsi-host 
             configuration: driver=sata_sil latency=64 
             resources: ioport:8440-8447 ioport:8434-8437 ioport:8438-843f ioport:8430-8433 ioport:8400-840f iomemory:b0004000-b00041ff irq:17 
           *-disk 
                description: SCSI Disk 
                product: TOSHIBA MK1234GS 
                vendor: ATA 
                physical id: 0.0.0 
                bus info: scsi@0:0.0.0 
                logical name: /dev/sda 
                version: AH00 
                serial: 37POFE1LS 
                size: 111GB 
                capabilities: partitioned partitioned:dos 
                configuration: ansiversion=5 
              *-volume:0 
                   description: Linux filesystem partition 
                   physical id: 1 
                   bus info: scsi@0:0.0.0,1 
                   logical name: /dev/sda1 
                   capacity: 109GB 
                   capabilities: primary bootable 
              *-volume:1 
                   description: Extended partition 
                   physical id: 2 
                   bus info: scsi@0:0.0.0,2 
                   logical name: /dev/sda2 
                   size: 2212MB 
                   capacity: 2212MB 
                   capabilities: primary extended partitioned partitioned:extended 
                 *-logicalvolume 
                      description: Linux swap / Solaris partition 
                      physical id: 5 
                      logical name: /dev/sda5 
                      capacity: 2212MB 
                      capabilities: nofs 
        *-usb:0 
             description: USB Controller 
             product: IXP SB400 USB Host Controller 
             vendor: ATI Technologies Inc 
             physical id: 13 
             bus info: pci@00:13.0 
             version: 80 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ohci bus_master 
             configuration: driver=ohci_hcd latency=64 
             resources: iomemory:b0005000-b0005fff irq:18 
           *-usbhost 
                product: OHCI Host Controller 
                vendor: Linux 2.6.20-16-generic ohci_hcd 
                physical id: 1 
                bus info: usb@1 
                logical name: usb1 
                version: 2.06 
                capabilities: usb-1.10 
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s 
        *-usb:1 
             description: USB Controller 
             product: IXP SB400 USB Host Controller 
             vendor: ATI Technologies Inc 
             physical id: 13.1 
             bus info: pci@00:13.1 
             version: 80 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ohci bus_master 
             configuration: driver=ohci_hcd latency=64 
             resources: iomemory:b0006000-b0006fff irq:18 
           *-usbhost 
                product: OHCI Host Controller 
                vendor: Linux 2.6.20-16-generic ohci_hcd 
                physical id: 1 
                bus info: usb@2 
                logical name: usb2 
                version: 2.06 
                capabilities: usb-1.10 
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s 
        *-usb:2 
             description: USB Controller 
             product: IXP SB400 USB2 Host Controller 
             vendor: ATI Technologies Inc 
             physical id: 13.2 
             bus info: pci@00:13.2 
             version: 80 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ehci bus_master cap_list 
             configuration: driver=ehci_hcd latency=64 
             resources: iomemory:b0007000-b0007fff irq:18 
           *-usbhost 
                product: EHCI Host Controller 
                vendor: Linux 2.6.20-16-generic ehci_hcd 
                physical id: 1 
                bus info: usb@3 
                logical name: usb3 
                version: 2.06 
                capabilities: usb-2.00 
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s 
        *-serial 
             description: SMBus 
             product: IXP SB400 SMBus Controller 
             vendor: ATI Technologies Inc 
             physical id: 14 
             bus info: pci@00:14.0 
             version: 83 
             width: 32 bits 
             clock: 66MHz 
             capabilities: cap_list 
             configuration: driver=piix4_smbus latency=0 
             resources: ioport:8410-841f iomemory:54180000-541803ff 
        *-ide:1 
             description: IDE interface 
             product: Standard Dual Channel PCI IDE Controller ATI 
             vendor: ATI Technologies Inc 
             physical id: 14.1 
             bus info: pci@00:14.1 
             version: 80 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ide bus_master cap_list 
             configuration: driver=ATIIXP_IDE latency=0 
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:8420-842f irq:19 
           *-ide 
                description: IDE Channel 0 
                physical id: 0 
                bus info: ide@0 
                logical name: ide0 
                clock: 66MHz 
              *-cdrom 
                   description: DVD-RAM writer 
                   product: MATSHITADVD-RAM UJ-850S 
                   physical id: 0 
                   bus info: ide@0.0 
                   logical name: /dev/hda 
                   version: 1.50 
                   serial: RA07 097266 
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram 
                   configuration: mode=udma2 
                 *-disc 
                      physical id: 0 
                      logical name: /dev/hda 
        *-multimedia 
             description: Audio device 
             product: SB450 HDA Audio 
             vendor: ATI Technologies Inc 
             physical id: 14.2 
             bus info: pci@00:14.2 
             version: 01 
             width: 64 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=HDA Intel latency=64 
             resources: iomemory:b0000000-b0003fff irq:19 
        *-isa 
             description: ISA bridge 
             product: IXP SB400 PCI-ISA Bridge 
             vendor: ATI Technologies Inc 
             physical id: 14.3 
             bus info: pci@00:14.3 
             version: 80 
             width: 32 bits 
             clock: 66MHz 
             capabilities: isa bus_master 
             configuration: latency=0 
        *-pci:3 
             description: PCI bridge 
             product: IXP SB400 PCI-PCI Bridge 
             vendor: ATI Technologies Inc 
             physical id: 14.4 
             bus info: pci@00:14.4 
             version: 80 
             width: 32 bits 
             clock: 66MHz 
             capabilities: pci subtractive_decode bus_master 
           *-network 
                description: Ethernet interface 
                product: RTL-8139/8139C/8139C+ 
                vendor: Realtek Semiconductor Co., Ltd. 
                physical id: 1 
                bus info: pci@06:01.0 
                logical name: eth0 
                version: 10 
                serial: 00:16:d4:d3:04:4d 
                size: 10MB/s 
                capacity: 100MB/s 
                width: 32 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s 
                resources: ioport:a000-a0ff iomemory:b0300000-b03000ff irq:20 
           *-pcmcia 
                description: CardBus bridge 
                product: CB-712/4 Cardbus Controller 
                vendor: ENE Technology Inc 
                physical id: 4 
                bus info: pci@06:04.0 
                version: 10 
                width: 32 bits 
                clock: 33MHz 
                capabilities: pcmcia bus_master cap_list 
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 
                resources: iomemory:b0301000-b0301fff irq:16 
           *-memory:0 UNCLAIMED 
                description: FLASH memory 
                product: ENE PCI Memory Stick Card Reader Controller 
                vendor: ENE Technology Inc 
                physical id: 4.1 
                bus info: pci@06:04.1 
                version: 01 
                width: 32 bits 
                clock: 33MHz (30.3ns) 
                capabilities: bus_master cap_list 
                configuration: latency=64 maxlatency=4 mingnt=1 
                resources: iomemory:b0300400-b030047f irq:10 
           *-system 
                description: Generic system peripheral 
                product: ENE PCI Secure Digital Card Reader Controller 
                vendor: ENE Technology Inc 
                physical id: 4.2 
                bus info: pci@06:04.2 
                version: 01 
                width: 32 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list 
                configuration: driver=sdhci latency=64 maxlatency=72 mingnt=32 
                resources: iomemory:b0300800-b03008ff irq:21 
           *-memory:1 UNCLAIMED 
                description: FLASH memory 
                product: FLASH memory: ENE Technology Inc: 
                vendor: ENE Technology Inc 
                physical id: 4.3 
                bus info: pci@06:04.3 
                version: 01 
                width: 32 bits 
                clock: 33MHz (30.3ns) 
                capabilities: bus_master cap_list 
                configuration: latency=64 maxlatency=4 mingnt=1 
                resources: iomemory:b0300c00-b0300c7f irq:10 
           *-memory:2 UNCLAIMED 
                description: FLASH memory 
                product: ENE Technology Inc 
                vendor: ENE Technology Inc 
                physical id: 4.4 
                bus info: pci@06:04.4 
                version: 01 
                width: 32 bits 
                clock: 33MHz (30.3ns) 
                capabilities: cap_list 
                configuration: latency=0 maxlatency=72 mingnt=32 
                resources: iomemory:b0300100-b03001ff irq:255 
     *-pci:1 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 101 
          bus info: pci@00:18.0 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:2 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] Address Map 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 102 
          bus info: pci@00:18.1 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:3 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] DRAM Controller 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 103 
          bus info: pci@00:18.2 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:4 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] Miscellaneous Control 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 104 
          bus info: pci@00:18.3 
          version: 00 
          width: 32 bits 
          clock: 33MHz

---

### Post by Lambert on 2007-10-02
It's the section that says -*network UNCLAIMED ... atheros etc..


I believe you need to install a package called linux-restricted-modules________. It has the driver packaged called madwifi which is needed for this device to work.

If you have a standard 7.04 version installed I believe the correct package is 

linux-restricted-modules-2.6.20-15-386

If you didn't install 7.04, it's a different one, I believe these are on the install disk if you pop that back in and use synaptic to find that package. Otherwise you will need to connect to the internet via hardwire and install the package.

Once you get that installed you should be able to just control wireless from network manager.

If you need to learn some basics about ubuntu, go to ubuntuguide.org and it will explain things such as installing applications etc...

---

### Post by gregboone on 2007-10-04
I have been busting my butt on this same issue with my Belkin F5D8010 (Airgo chipset) PCMCIA card wireless.  

It does not list wireless on the network manager, so I have no option of wireless.

I look at hosts and it shows it listed as 127.0.1.1 as Ubuntu Belkin.

R/ Greg

---

### Post by klaasvanschelven on 2007-10-17
I have the same problem.... I've installed both 
 linux-restricted-modules for my kernel and
madwifi-tools   "tools for the Multiband Atheros Driver for WiFi"

I have Ubuntu 7.10 (yes I know I'm a day early, but it's the only thing that I got to work to some degree). 

This is what lshw has to say:

klaas@thinkpad:~$ sudo lshw -C network
[sudo] password for klaas:
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:1a:6b:67:85:ca
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.2.102 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

---

### Post by justinmiller87 on 2008-03-02
> **gregboone said:**
> I have been busting my butt on this same issue with my Belkin F5D8010 (Airgo chipset) PCMCIA card wireless.  

It does not list wireless on the network manager, so I have no option of wireless.

I look at hosts and it shows it listed as 127.0.1.1 as Ubuntu Belkin.

R/ Greg
Greg,

If you are still having issues, check the Airgo link in my signature. It is the card you have.

---

