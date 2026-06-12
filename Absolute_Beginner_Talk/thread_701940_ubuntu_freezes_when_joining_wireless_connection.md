---
title: "ubuntu freezes when joining wireless connection"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by 1adam12gb12 on 2008-02-19
Everything works fine on unsecured networks, but when I enter a pass phrase my HP Pavilion freezes. The caps lock blinks and I have to remove the battery to reboot. Whats up please?
 
"When we find ourselves in the majority, we must stop and reflect."- Mark Twain

---

### Post by jan quark on 2008-02-20
some input would be nice

Please run these terminal commands and post the output here:

```
lspci
```

```
sudo lshw
```

```
iwconfig
```

```
ifconfig
```

```
sudo iwlist scan
```

---

### Post by 1adam12gb12 on 2008-02-26
Thanks, Next time I try to connect to a secure network, I will gather that info. Here is a real newbie question. How do I create those code frames and paste the info into them?

---

### Post by 1adam12gb12 on 2008-02-29
Ok, Here is the info;
```
lspci-00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Bridge: VIA Technologies, Inc. VT8235 ACPI (rev 10)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 20)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

```
```

sudo lshw-    description: Portable Computer
    product: HP Pavilion Notebook PC
    vendor: Hewlett-Packard
    version: HP Pavilion Notebook ZE1000
    serial: TW22417055
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=portable uuid=807BF1C2-8984-D611-B6EF-00C09F0BB984
  *-core
       description: Motherboard
       product: HP Pavilion Notebook PC
       vendor: Hewlett-Packard
       physical id: 0
       version: HP Pavilion Notebook ZE1000
       serial: TW22417055
       slot: Service ID : 12198
     *-firmware:0
          description: BIOS
          vendor: Insyde Software
          physical id: 0
          version: JB.M1.31 (09/25/2002)
          size: 88KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot socketedrom edd int13floppynec int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: mobile AMD Athlon(tm) XP 1800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.0
          serial: 0
          slot: SCKT-A
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts fid vid cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KB
             capabilities: burst pipeline-burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 256KB
             capacity: 256KB
             capabilities: burst pipeline-burst external write-back
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3 Cache
     *-firmware:1
          description: BIOS
          vendor: @
          physical id: 4f4c
          version: (0)
          size: 894KB
          capacity: 2MB
          capabilities: eisa pnp escd bootselect int13floppy360 acpi i2oboot ieee1394boot biosbootspecification netboot
     *-memory:0 UNCLAIMED
          physical id: 1
        *-bank UNCLAIMED
             description: DIMM DRAM Synchronous 1027 MHz (1.0 ns) [empty]
             vendor: 2
             physical id: 0
             serial: 3
             slot: DRAM Slot 0
             width: 64 bits
             clock: 1027MHz (1.0ns)
     *-memory:1 UNCLAIMED
          physical id: 2
        *-bank UNCLAIMED
             description: DIMM DRAM Synchronous 1027 MHz (1.0 ns)
             vendor: 2
             physical id: 0
             serial: 3
             slot: DRAM Slot 1
             size: 256MB
             width: 64 bits
             clock: 1027MHz (1.0ns)
     *-memory:2 UNCLAIMED
          physical id: 3
        *-bank UNCLAIMED
             description: DIMM DRAM Synchronous 1027 MHz (1.0 ns)
             vendor: 2
             physical id: 0
             serial: 3
             slot: DRAM Slot 2
             size: 128MB
             width: 64 bits
             clock: 1027MHz (1.0ns)
     *-memory:3 UNCLAIMED
          physical id: 5
        *-bank UNCLAIMED
             description: TSOP VRAM 1027 MHz (1.0 ns) [empty]
             vendor: 2
             physical id: 0
             serial: 3
             slot: Video Memory
             width: 64 bits
             clock: 1027MHz (1.0ns)
     *-memory:4 UNCLAIMED
          physical id: 6
        *-bank UNCLAIMED
             description: TSOP SRAM 1027 MHz (1.0 ns)
             vendor: 2
             physical id: 0
             serial: 3
             slot: Cache SRAM
             size: 256KB
             width: 64 bits
             clock: 1027MHz (1.0ns)
     *-memory:5 UNCLAIMED
          physical id: 7
        *-bank UNCLAIMED
             description: TSOP EEPROM 1027 MHz (1.0 ns) [empty]
             vendor: 2
             physical id: 0
             serial: 3
             slot: Flash BIOS U43
             width: 16 bits
             clock: 1027MHz (1.0ns)
     *-memory:6 UNCLAIMED
          physical id: 8
     *-memory:7 UNCLAIMED
          physical id: 9
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 80
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=72 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=4
        *-pcmcia
             description: CardBus bridge
             product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=72 maxlatency=4 mingnt=8 module=ohci1394
        *-isa
             description: ISA bridge
             product: VT8231 [PCI-to-ISA Bridge]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=VIA_IDE latency=64 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK3018GAP
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: M2.01 A
                   serial: 52C51488T
                   size: 27GB
                   capacity: 27GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 26GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 1058MB
                      capacity: 1058MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 1058MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: QSI CD-RW/DVD-ROM SBW-081
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: NH02
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2 status=nodisc
        *-usb
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.2
             bus info: pci@0000:00:11.2
             version: 1e
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=22 module=uhci_hcd
        *-bridge UNCLAIMED
             description: Bridge
             product: VT8235 ACPI
             vendor: VIA Technologies, Inc.
             physical id: 11.4
             bus info: pci@0000:00:11.4
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0 module=snd_via82xx_modem
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 51
             serial: 00:c0:9f:0b:b9:84
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=16 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
     *-network
          description: Wireless interface
          product: RTL8180L 802.11b MAC
          vendor: Realtek Semiconductor Co., Ltd.
          physical id: a
          bus info: pci@0000:02:00.0
          logical name: wlan0
          version: 20
          serial: 00:09:5b:63:60:17
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=rtl8180 ip=198.104.23.119 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b linked
  *-battery
       product: DR36
       vendor: Duracell
       physical id: 1
       version: 01/06/97
       serial: 0042
       slot: Smart Battery Conn J37
       configuration: voltage=0.0V

```

```
iwconfig-lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b  Mode:Managed  Frequency:2.432 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   Sensitivity=80/85  
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=14/100  Signal level=-124 dBm  Noise level=-170 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
```
ifconfig-eth0      Link encap:Ethernet  HWaddr 00:C0:9F:0B:B9:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:63:60:17  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:54 overruns:0 frame:0
          TX packets:771 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 b)  TX bytes:24842 (24.2 KB)
          Interrupt:11 Memory:d7c72000-d7c72100 

```
```
sudo iwlist scan-lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:DF:EB:3A
                    ESSID:"Terra Bite"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:137  Signal level:0  Noise level:25
                    Extra: Last beacon: 1ms ago
          Cell 02 - Address: 00:14:6C:F7:40:D0
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:147  Signal level:0  Noise level:34
                    Extra: Last beacon: 1325ms ago
          Cell 03 - Address: 00:19:CB:3A:77:A4
                    ESSID:"Heathman Hotel"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:138  Signal level:0  Noise level:28

```

---

### Post by Tezac on 2008-04-27
I am having the exact same thing happen to me. I am using Dell Inspiron with Linksys WPC11 PCIMA card. I can see my WEP network listed but system just locks up when try to connect using HEX key. I have Caps Lock and also Scroll Lock flashing when locked up. Have to reboot to gain access after it happens. It is a new installation of ubuntu, just switched from XP. It worked fine in XP but I don't want to go back to Microsoft software. I am looking forward to the solution.

---

