---
title: "Wireless card not detected sometimes"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by cool_penguin on 2007-11-28
Hi Guys, 
I am using Gusty.  My problem is ... my computer doesn't detect my wireless card at boot sometimes. When it is detected, wireless works flawlessly, though.

So, sometimes I boot, and the cards detected and wireless works fine. Other times, it's not detected, and I do "iwconfig" in console, all I see is... (I cannot see available wireless networks when i click on the network applet icon)

lo        no wireless extensions.

eth1      no wireless extensions.

When the card is detected fine, I see the following with "iwconfig" (I can see available wireless networks when i click on the network applet icon)

lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MyNet"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:3F:84:A3:59
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-57 dBm  Noise level=-94 dBm
          Rx invalid nwid:15267  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

why is my computer randomly detecting / not-detecting my wireless?

I also observed something strange. When i go to Restricted driver manager and disable Atheros Hardware Access Layer (HAL) and re-boot my system, i can see available wireless networks when i click on the network applet icon. 

After an overnight shutdown of my computer, i again cannot see my available wireless networks. So, i went back to the Restricted driver manager and enabled Atheros Hardware Access Layer (HAL) and re-booted my system and then i can see available wireless networks when i click on the network applet icon. 

I am confused and dont know whats going on here. I am planning to get myself a wifi router, but with this problem looks like i have to be using the wired ethernet connection till the problem gets resolved. 

Any help from you guys will be greatly appreciated. 

Thanks a lot.

Cheers,
Harry

---

### Post by zabien1970 on 2007-11-28
Just thinking it could be a loose or dirty connection, I would try unplugging it and wiping off the connectors and replugging in, even wiggle it around a little

---

### Post by cool_penguin on 2007-11-28
Its an inbuilt card.

---

### Post by ukripper on 2007-11-28
> **cool_penguin said:**
> Hi Guys, 
I am using Gusty.  My problem is ... my computer doesn't detect my wireless card at boot sometimes. When it is detected, wireless works flawlessly, though.

So, sometimes I boot, and the cards detected and wireless works fine. Other times, it's not detected, and I do "iwconfig" in console, all I see is... (I cannot see available wireless networks when i click on the network applet icon)

lo        no wireless extensions.

eth1      no wireless extensions.

When the card is detected fine, I see the following with "iwconfig" (I can see available wireless networks when i click on the network applet icon)

lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MyNet"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:3F:84:A3:59
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-57 dBm  Noise level=-94 dBm
          Rx invalid nwid:15267  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

why is my computer randomly detecting / not-detecting my wireless?

I also observed something strange. When i go to Restricted driver manager and disable Atheros Hardware Access Layer (HAL) and re-boot my system, i can see available wireless networks when i click on the network applet icon. 

After an overnight shutdown of my computer, i again cannot see my available wireless networks. So, i went back to the Restricted driver manager and enabled Atheros Hardware Access Layer (HAL) and re-booted my system and then i can see available wireless networks when i click on the network applet icon. 

I am confused and dont know whats going on here. I am planning to get myself a wifi router, but with this problem looks like i have to be using the wired ethernet connection till the problem gets resolved. 

Any help from you guys will be greatly appreciated. 

Thanks a lot.

Cheers,
Harry

Can you piost output of following:
```
sudo lshw
```

---

### Post by cool_penguin on 2007-11-28
this is the output i got. (this was when my wireless was working by chance)


harish-laptop             
    description: Computer
    product: TravelMate 2310
    vendor: Acer, inc.
    version: Not Applicable
    serial: LXTAF0C0075310C712EM00
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=4068195C-BC87-D811-8052-00C09FBF64DD
  *-core
       description: Motherboard
       product: Lugano
       vendor: Acer, Inc.
       physical id: 0
       version: Not Applicable
       serial: LXTAF0C0075310C712EM00
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: 3A14 (09/13/05)
          size: 100KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video usb
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: Socket 479M
          size: 1400MHz
          capacity: 1400MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up
        *-cache
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 1280MB
          capacity: 3GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM1
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM2
             size: 1GB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM [empty]
             physical id: 2
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=64 module=sis_agp
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-disk
                description: SCSI Disk
                product: HTS424040M9AT00
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MA2O
                serial: MPA248Q2C4GYUL
                size: 37GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 37GB
                   capacity: 37GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 27GB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 454MB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 9044MB
           *-cdrom
                description: DVD reader
                product: COMBO SOSC-2483K
                vendor: Slimtype
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KCK2
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=173 maxlatency=11 mingnt=52
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=173 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80 module=ehci_hcd
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:c0:9f:bf:64:dd
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=83.219.96.96 latency=173 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-network:1
             description: Wireless interface
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: wifi0
             version: 01
             serial: 00:14:a4:12:5f:34
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


Hope u guys can help me.

Thanks a lot.

---

