---
title: "Ubuntu freezes up..."
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Jason2gs on 2008-04-08
I know that sounds like a very vague description, but just hear me out.

I'll be on the computer like normal, and all of a sudden, Ubuntu will decide to freeze up on me. I won't be able to do anything except from inside the window that was active at the time of the crash.

Sometimes it'll fix itself for a few moments, long enough for me to log out/log in, and it'll sometimes be good. Other times I'll have to completely restart the computer.

Although that's annoying, it's not as bad as the times where I have to flip the laptop on it's side and pop the battery out.

I hate doing that, of course, but sometimes it's the only way to render the computer usable.

Is this a known problem? Is it perhaps fixed in Hardy Heron?

Thanks,

-Mike

---

### Post by wpshooter on 2008-04-08
Do you have any other O/S on this computer ?  If so, are you have any similar problems when running that O/S ?

---

### Post by Jason2gs on 2008-04-08
I do now, but I had this problem long before I installed it.

---

### Post by arbulus on 2008-04-08
Are you using the 3D desktop effects? If your machine is low on resources, those can cause freezes from time to time.

---

### Post by Jason2gs on 2008-04-08
I'm using no other effects than what came default with Ubuntu.

---

### Post by jseiser on 2008-04-08
If you had this problem before ubuntu etc, its probably a hardware issue.  Even if this problem didnt happen before ubuntu, I would still check to make sure its not a hardware issue.  First off, run memtest, this comes with the alternative install of ubuntu ( might come with live cd) that will run through and check your ram.  The next thing to run would be a program to check the harddisk ( at work we use Spinrite, but its closed source and costs $) I tried to quickly google an opensource replacement and this came up, [http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html) - its available in ubuntu as ddrescue.

---

### Post by arbulus on 2008-04-08
> **Jason2gs said:**
> I'm using no other effects than what came default with Ubuntu.

Go to System > Preferences > Appearance.  The last tab in that windows should be called "Effects" I believe.  Go to that one and see what selection is checked.  If "Basic Effects" is checked, change it to "None" and see if that helps.

---

### Post by Jason2gs on 2008-04-08
Jseiser,

I mean I had the problem in Ubuntu, before I installed a second OS.

And thank you for the reply, Arbulus :)

Just checked and I have no effects turned on.

I am using GNOME, however, which has some effects of it's own. (Such as that annoying black frame around windows when they're minimizing. Ugly as heck...)

---

### Post by ShodanjoDM on 2008-04-08
Can you post your h/w spec? I'll see if I can help starting from that.

---

### Post by Jason2gs on 2008-04-08
```
mike@Juankubariz:~$juankubariz               
    description: Notebook
    product: Presario V5000 (RG324UA#ABA)
    vendor: Hewlett-Packard
    version: F.43
    serial: CND63613GL
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=B3F88BAA-3AC3-11DB-948C-0016D4429375
  *-core
       description: Motherboard
       product: 30AE
       vendor: Hewlett-Packard
       physical id: 0
       version: 49.56
       serial: CND63613GL
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.43 (08/18/2006)
          size: 103KB
          capacity: 448KB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot smartbattery
     *-cpu
          description: CPU
          product: Mobile AMD Sempron(tm) Processor 3300+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          slot: U23
          size: 2GHz
          capacity: 2GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 128KB
             capacity: 1MB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 128KB
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: JP11
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: JP30
             size: 512MB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga bus_master cap_list
                configuration: latency=66 mingnt=8
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=0 module=atiixp
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD600UE-22KVT0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 01.03K01
                   serial: WD-WXE506839844
                   size: 55GB
                   capacity: 55GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 2000MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 49GB
                      capabilities: primary
                 *-volume:2
                      description: Extended partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      size: 4777MB
                      capacity: 4777MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 4777MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD reader
                   product: TSSTcorpCDW/DVD TS-L462D
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: HS00
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: status=nodisc
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:06:02.0
                logical name: eth1
                version: 02
                serial: 00:14:a5:e9:33:b9
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22.9 ip=192.168.1.100 latency=64 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 6
                bus info: pci@0000:06:06.0
                logical name: eth0
                version: 10
                serial: 00:16:d4:42:93:75
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
        *-communication
             description: Modem
             product: SB400 AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi generic bus_master cap_list
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2 module=snd_atiixp_modem
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
  *-battery
       physical id: 1
       slot: Left Front

```

Don't know exactly what hardware specs you need. Sorry ^_^

---

### Post by ShodanjoDM on 2008-04-08
Thanks, just what I need. I was thinking that you might be using some off brands or old laptop but then it's not.

Here's what I found so far:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107115](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107115)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/138408](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/138408)

There might be some fixes/workarounds since some posters there also have the same laptop as yours. I didnt read all the posts, though, sorry :(

---

### Post by Jason2gs on 2008-04-08
Hm, thank you :)

Happen to know if there's a name for the bug? "Ubuntu freezes up" doesn't bring back a solution to my particular problem :) (It may, actually. i just don't feel like clicking through each one.)

---

### Post by ShodanjoDM on 2008-04-08
> **Jason2gs said:**
> Hm, thank you :)

Happen to know if there's a name for the bug? "Ubuntu freezes up" doesn't bring back a solution to my particular problem :) (It may, actually. i just don't feel like clicking through each one.)

I just googled for: 
```
Ubuntu crash "Presario V5000"
```

or

```
Gutsy gdm bug "Presario V5000"
```

:D

---

### Post by Vadi on 2008-04-08
I had issues with the freezing up when using ndiswrapper on a poor connection. I guess the connection would go weak and Ubuntu hiccups.

Definitely not an issue with Compiz though.

---

