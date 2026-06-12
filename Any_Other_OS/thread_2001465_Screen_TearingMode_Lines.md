---
title: "Screen Tearing/Mode Lines"
date: 2012-06-10
forum: Any Other OS
---

### Post by Fait on 2012-06-10
Linux Mint 13 Maya LTS 64-Bit Cinnamon

VPCCW21FX

Here [http://store.sony.com/webapp/wcs/stores ... ifications]("http://store.sony.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&partNumber=VPCCW21FX/L#specifications")

I  have screen tearing such that the top half inch of my screen flickers  during video playback, the more motion - the more noticable. I have the  nvidia proprietary driver installed and it seems properly configured  (the logo appears on boot and the settings gui appears to work) I have  tried the open source driver and it has the same symptoms. I need 3D  support in any case. Prior to Linux Mint/Cinnamon I have used many other  window managers openbox, awesome, xmonad; performance of video playback  was much worse with tearing throughout the whole frame. I suspect the  use of compiz in Linux Mint has reduced the problem to its current  symptom. I suspect it is my monitor/lack of configuration. My backlight  is not recognized by my GeForce 310 mobile card so currently I am using  the "nvidia_bl" package. 

I am open to ALL sugestions except "get a new laptop" thats already on my list but not affordable for a couple years.
HOWEVER,  if it is feasable to purchase a compatable monitor without this problem  and install it in my current laptop, I am open to it.

Of course,  I would rather solve this with configuration/additional software. I  have read some material mentioning it is a lack of properly configured  "mode lines" The material I could find was a bit too technical without  some kind of primer, so any help in understanding or configuring would  be very appreciated. Ultimatly I would like any info on how to get my  monitor fully or more fully recognized by my graphics card to the effect  of fixing screen tearing, backlight functionality, and achive normal  expected operating function.

All help is desperatly requested and deeply appreciated, thank you to all who take their time to help us who need assistance.  [IMG]http://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG] .

EDIT: Solved

---

### Post by Fait on 2012-06-10
Linux Mint 13 Maya LTS 64-Bit Cinnamon

VPCCW21FX

Here [http://store.sony.com/webapp/wcs/stores ... ifications]("http://store.sony.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&partNumber=VPCCW21FX/L#specifications")

I  have screen tearing such that the top half inch of my screen flickers  during video playback, the more motion - the more noticable. I have the  nvidia proprietary driver installed and it seems properly configured  (the logo appears on boot and the settings gui appears to work) I have  tried the open source driver and it has the same symptoms. I need 3D  support in any case. Prior to Linux Mint/Cinnamon I have used many other  window managers openbox, awesome, xmonad; performance of video playback  was much worse with tearing throughout the whole frame. I suspect the  use of compiz in Linux Mint has reduced the problem to its current  symptom. I suspect it is my monitor/lack of configuration. My backlight  is not recognized by my GeForce 310 mobile card so currently I am using  the "nvidia_bl" package. 

I am open to ALL sugestions except "get a new laptop" thats already on my list but not affordable for a couple years.
HOWEVER,  if it is feasable to purchase a compatable monitor without this problem  and install it in my current laptop, I am open to it.

Of course,  I would rather solve this with configuration/additional software. I  have read some material mentioning it is a lack of properly configured  "mode lines" The material I could find was a bit too technical without  some kind of primer, so any help in understanding or configuring would  be very appreciated. Ultimatly I would like any info on how to get my  monitor fully or more fully recognized by my graphics card to the effect  of fixing screen tearing, backlight functionality, and achive normal  expected operating function.

All help is desperatly requested and deeply appreciated, thank you to all who take their time to help us who need assistance.  [IMG]http://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG] .

---

### Post by drs305 on 2012-06-10
Fait,

Welcome to the Ubuntu Forums.

I've merged your duplicate threads. Please do not post multiple threads on the same topic as it complicates our ability to help you.

I'd like to be able to help but don't have a suggestion for your issue.

---

### Post by drawkcab on 2012-06-11
1.  Check the settings on compiz if it is enabled.  You want it set to vsync with the refresh rate on your monitor.

2.  Better yet dump compiz if you don't really need it and use the compositor native to Gnome, Xfce or KDE.

3.  Check your video driver settings.  Make sure your image is set to centered and that the card is set to vsync with your monitor.

4.  Make sure that you have correct codecs installed, especially if you're watching high def .mkv formats.  I keep 5 or 6 different media players around because each works differently with different formats.  Also, check the settings of your media players to enable them to offload video processing to the gpu whenver possible.  

These are just some ideas of the things you can tinker with.  Since I've left compiz behind about a year ago, upgraded my codecs and matched media players to the kind of files I play (thanks umplayer) many of the pesky video tearing problems that dogged me in 11.04 are behind me.

---

### Post by qyot27 on 2012-06-11
It can be the result of using lesser video output drivers (not to be confused with the driver/kernel module for your video card).  Xv is notorious for tearing, and is usually the default for media players on Linux, probably for historical or compatibility reasons more than anything; if possible, use gl or vdpau.

The way to select this might vary with the player, but for mplayer it's the -vo option (in the various GUIs for mplayer it'd be somewhere in Preferences; look for a 'Video output' dropdown menu).  For better vdpau support it would be advisable to use mplayer2, provided that you're not already using it.

---

### Post by Fait on 2012-06-11
1&2: I have been informed that compiz is incompatable with cinnamon so it must use   something else

3: Been tinkering for years, double checked that vsync is selected and I changed resolution from auto to centered @1366x768.

4: Everything does it, every player including flash player (vlc, mplayer, smplayer, gnome mplayer, banshee, movie player) everything I've ever tried. With or without vdpau.

Thanks for the suggestions.

System:    Host: gizmatron Kernel: 3.2.0-23-generic x86_64 (64 bit, gcc: 4.6.3) Desktop: Gnome Distro: Linux Mint 13 Maya
Graphics:  Card: NVIDIA GT218 [GeForce 310M] bus-ID: 01:00.0 X.Org: 1.11.3 driver: nvidia Resolution: 1366x768@50.0hz 
           GLX Renderer: GeForce 310M/PCIe/SSE2 GLX Version: 3.3.0 NVIDIA 295.49 Direct Rendering: Yes

Shouldn't it be @ 60.0hz?

---

### Post by drawkcab on 2012-06-11
Check your monitor hardware, but yeah, I think most lcd panels are at 60.  That would explain your problem.

---

### Post by Fait on 2012-06-11
I don't know how to check what my native refresh rate for my monitor is but I can say that in nvidia settings it says 60hz and in another section 59.94hz which I assume means the first number is rounded.

I don't know how I would go about forcing it to use the proper number and I would also like to know for 100% that it is 60hz (I have a laptop).

---

### Post by qyot27 on 2012-06-11
I'm not sure if the typical issues in Hz with analog equipment apply to LCDs, but Europe uses 50Hz connections in its electrical wiring, which is why the PAL television standard(s) broadcast at 25p/50i.  It's not inconceivable to think this might apply to computer monitors as well, and got grandfathered in when LCDs took over.

If that's *not* relevant to either LCDs or to this particular issue, then it may be a hardware issue, or it could be that it's just getting misreported with no otherwise adverse effect.


Cinnamon is a fork of Gnome Shell, and accordingly, it uses Muffin (itself a fork of Mutter, Gnome Shell's window manager).

---

### Post by qyot27 on 2012-06-11
> **Fait said:**
> I don't know how to check what my native refresh rate for my monitor is but I can say that in nvidia settings it says 60hz and in another section 59.94hz which I assume means the first number is rounded.

I don't know how I would go about forcing it to use the proper number and I would also like to know for 100% that it is 60hz (I have a laptop).
59.94 and 60 are more or less interchangeable.  You don't have to worry about that.  The same thing happens with 29.97/30 and 23.976/24 when referring to television and film framerates.  One's a technically-correct form and the other is shorthand.


I'd imagine that you could use *sudo lshw* to check the native refresh rate, but I'm not sure.

---

### Post by Fait on 2012-06-11
```
gizmatron                 
    description: Notebook
    product: VPCCW21FX (N/A)
    vendor: Sony Corporation
    version: C603VY4U
    serial: 27506731-3055971
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=notebook family=VAIO sku=N/A uuid=E0DE9494-AE0F-DF11-844F-0024BEBE9AB5
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: R0170Y7
          date: 05/14/2010
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
          serial: N/A
          slot: N/A
          size: 1333MHz
          capacity: 2133MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-through
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3
             physical id: 0
             slot: SODIMM1
             size: 4GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR3
             physical id: 1
             slot: SODIMM2
             size: 4GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:d0000000-e30fffff
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 310M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:d000(size=128) memory:e3000000-e307ffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:16 memory:e3080000-e3083fff
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:e8e08000-e8e083ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:e8e00000-e8e03fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:c000(size=4096) memory:e7a00000-e8dfffff ioport:e9500000(size=2097152)
           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6230
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 34
                serial: 88:53:2e:b4:2b:f7
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=18.168.6.1 ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:43 memory:e7a00000-e7a01fff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:b000(size=4096) memory:e6600000-e79fffff ioport:e9300000(size=2097152)
           *-generic:0
                description: SD Host controller
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:e6603000-e66030ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: Memory Stick Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:e6602000-e66020ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 PCIe IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.3
                bus info: pci@0000:03:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:16 memory:e6601000-e66017ff
           *-generic:2
                description: SD Host controller
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0.4
                bus info: pci@0000:03:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:19 memory:e6600000-e66000ff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:a000(size=4096) memory:e5200000-e65fffff ioport:e9100000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8057 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 10
                serial: 00:24:be:be:9a:b5
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:42 memory:e5220000-e5223fff ioport:a000(size=256) memory:e5200000-e521ffff
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:9000(size=4096) memory:e3200000-e51fffff ioport:e8f00000(size=2097152)
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e8e07000-e8e073ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:e070(size=8) ioport:e060(size=4) ioport:e050(size=8) ioport:e040(size=4) ioport:e020(size=32) memory:e8e06000-e8e067ff
           *-disk
                description: ATA Disk
                product: ST9500325AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0004
                serial: 5VE7HVFR
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000505f4
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   capacity: 9536MiB
                   capabilities: primary bootable
                   configuration: mount.fstype=btrfs mount.options=rw,relatime,nospace_cache state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 456GiB
                   capacity: 456GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8010MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /var
                      capacity: 9536MiB
                      configuration: mount.fstype=btrfs mount.options=rw,relatime,nospace_cache state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /tmp
                      capacity: 18GiB
                      configuration: mount.fstype=btrfs mount.options=rw,relatime,nospace_cache state=mounted
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /home
                      capacity: 420GiB
                      configuration: mount.fstype=btrfs mount.options=rw,relatime,nospace_cache state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT20N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: CL08
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:e8e05000-e8e050ff ioport:e000(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@2:1.1
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Desktop
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
             version: 0130
             serial: 2GHJCET2
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=03a11268
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@8:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/Seagate 1TB
                version: 1.0
                serial: 7159c174-86a0-419f-8254-d57b51453d9a
                size: 931GiB
                capacity: 931GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-06-10 14:53:35 filesystem=ext4 label=Seagate 1TB lastmountpoint=/media/Seagate 1TB modified=2012-06-11 00:24:02 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,user_xattr,barrier=1,data=ordered mounted=2012-06-11 00:24:02 state=mounted

```Thanks for the info, any idea how I can specify the correct refresh rate? xorg.conf maybe?

I'm in the U.S. by the way.

---

### Post by qyot27 on 2012-06-11
The correct rate meaning forcing it to not say 50Hz?  I wouldn't know.  Like I said, that could just be a graphical bug that displays an incorrect number but doesn't affect the underlying operation at all.

In the case of 59.94/60, the screen treats both of them as essentially the same number, since the difference is so marginal (60000/1000 vs. 60000/1001) that the display handles both of them under the same mode.

> 4: Everything does it, every player including flash player (vlc, mplayer, smplayer, gnome mplayer, banshee, movie player) everything I've ever tried. With or without vdpau.
But what about gl?  Triple buffering should also be used if vsync is enabled, if I'm remembering the normal configuration advice correctly.

That said, half of that list are just frontends to mplayer.  Banshee and Movie Player (which is what I assume is Totem) use gstreamer, but ultimately, the decoding in all of these cases will be coming from the FFmpeg libraries, unless it's being sent to the GPU using vdpau (and the file is properly able to be accelerated - it depends on what format the video is and what features it was encoded with).  The frontends just provide a nice sheen, and - except in certain awful cases like VLC - shouldn't interfere with the underlying decoding or display process.

Of course, I'll also take the time to note right now that I don't think we can expect a perfectly non-tearable playback experience on Linux until Wayland matures enough for distros and the media players and display drivers to switch over to it directly and leave X behind.  Or at least one can hope.

---

### Post by Fait on 2012-06-11
So I came up with

Modeline       "1360x768@52" 72.00 1360 1392 1664 1696 768 784 791 807 -hsync +vsync

After some research on my monitor

B140XW02 V.1 specs[]("http://www.yslcd.com.tw/docs/product/")

Google First Result

and a calculator

Here:

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

and some help with xorg.conf

Here:

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/192290](https://answers.launchpad.net/ubuntu/+source/xorg/+question/192290)

Didn't work, I might have done something wrong or it could be something else. My monitor works fine but I still have my original problem. Tearing in the form of a flicker that covers the top half inch to 1 inch of my screen. Invisible during still shots and progressively worse as motion increases.

I also tried your advice on using gl. Configured vlc and smplayer. No change. If you could explain where and how to enable triple buffering? Thanks for the support.

---

### Post by qyot27 on 2012-06-11
Actually in SMPlayer it's *Double* buffering, not Triple (and it's on the same Video tab as the output module selector).  I was thinking of video game emulators.  Also in the SMPlayer configuration, you could try to uncheck 'Draw video using slices' so that it renders the entire frame at once.

In VLC, you have to tell it to show All options, go down to the Output modules under Video, and then look at each module to see if any of them have a Triple (or Double) buffering option.

---

### Post by Fait on 2012-06-11
Already enabled.

Well, here's to hoping wayland becomes everything we hope it will be. I just hope linux mint embraces it, if they don't I guess I'll just have to spend a little more time configuring ubuntu. Anyone know when wayland is projected to become standard?

---

### Post by qyot27 on 2012-06-12
As Wayland is still in its formative stages, I wouldn't expect it getting serious traction until at least 13.10, although that could just be overall pessimism on my part (but hey, Wayland has better chances of seeing a mature release in a couple years than ReactOS does of having a beta release in the same time...).  I'd be rather confident that by the time Ubuntu and Fedora take the plunge, most of the power-user distros would have already had it for some time.  And since Mint is based on Ubuntu (or Debian, in the case of LMDE), it's probably a fairly accurate statement that once it's pushed to the forefront in either of those two, it'll be in Mint in short order (and if Debian goes first, then the same thing applies to Ubuntu in a lot of ways also).

There is at least this:
[http://sourceforge.net/projects/rebeccablackos/](http://sourceforge.net/projects/rebeccablackos/)

It's meant to be a Wayland Live CD.  There's also [video evidence on YouTube](http://www.youtube.com/watch?v=zqbnsfORb3g) of mplayer running under Wayland, although I have no clue about the underlying OS setup involved.

I'm going off of its stated design goals as I haven't tested Wayland at all.  This is partially because I'm not sure if my graphics card is okay with the OpenGL ES 2.0 requirement; if it can interwork fine with normal OpenGL 2.0-supporting cards, then it *should*, but I've learned not to automatically expect that it *will*.

---

### Post by Fait on 2012-06-12
Thanks for the info. I've spent the last couple hours dream shopping for a new laptop. I think I'm going to switch over to Ubuntu since I want to buy my laptop with linux preinstallled + Ubuntu is most popular + they have explicitly stated wayland as the future + Linux Mint is a skip and a jump from it anyway. Any recommendations for buying a non-windows-mac laptop? Bare bones, Do-It-Yourself, Linux Preinstalled? I'm looking in the high-end market, I can install things like the wi-fi, disc drive, RAM, hard drive, etc. But I would like to purchase it assembled with the motherboard, cpu, gpu, monitor, anything one wouldn't think of as upgradeable. If it comes with linux already on it or certified that the components are linux compatable that would be a huge plus. Price doesn't really matter, I would rather save another year then get something that isn't exactly what I want so sub 5k is my range. Ubuntu or Tux meta key would be cool. If this isn't your area of expertise, I understand. It'll be a couple years before I can buy it. I'm looking around so that I have an idea of where to go/ what to do to get the best Linux experience when I am ready to purchase.

Is there a way to rep you? You've been very helpful.

---

### Post by Dlambert on 2012-06-12
Cinnamon is also in a very early stage compared to GNOME or KDE. SO it may just be a bug. Have you tried XFCE or LXDE?

---

### Post by Dlambert on 2012-06-12
> **Fait said:**
> Thanks for the info. I've spent the last couple hours dream shopping for a new laptop. I think I'm going to switch over to Ubuntu since I want to buy my laptop with linux preinstallled + Ubuntu is most popular + they have explicitly stated wayland as the future + Linux Mint is a skip and a jump from it anyway. Any recommendations for buying a non-windows-mac laptop? Bare bones, Do-It-Yourself, Linux Preinstalled? I'm looking in the high-end market, I can install things like the wi-fi, disc drive, RAM, hard drive, etc. But I would like to purchase it assembled with the motherboard, cpu, gpu, monitor, anything one wouldn't think of as upgradeable. If it comes with linux already on it or certified that the components are linux compatable that would be a huge plus. Price doesn't really matter, I would rather save another year then get something that isn't exactly what I want so sub 5k is my range. Ubuntu or Tux meta key would be cool. If this isn't your area of expertise, I understand. It'll be a couple years before I can buy it. I'm looking around so that I have an idea of where to go/ what to do to get the best Linux experience when I am ready to purchase.

Is there a way to rep you? You've been very helpful.

[URL="https://www.system76.com/?gclid=CNOa9vnlyLACFYpgTAodyQ-0Ww"]Systems76 https://www.system76.com/?
gclid=CNOa9vnlyLACFYpgTAodyQ-0Ww[/URL]

Or [Zareason http://zareason.com/shop/home.php?cat=]("http://zareason.com/shop/home.php?cat=")

---

### Post by Fait on 2012-06-12
Thanks for the links, given that I want to wait until the next LTS before a new purchase I think I'm going to build my own. Just going over it in my head is daunting but: I have a long time to wait, I will learn alot, I get to handpick every part, and I can add in things like A grade thermal paste and heat spreaders; larger capacity fans that are quieter and so on. I've never built a laptop from scratch but I think I'll enjoy the challenge. I'm going to install Ubuntu tonight. I'll give Unity a shot but if I don't like it, I see how much effort it takes to install cinnamon or mate.

System76 - Every laptop seemed to have an HD4000 chip, why? For the money you can spend in upgrades like top of the line core I7, why can I not have even a basic nvidia card?

ZaReason - Is like every other retailer that I like, good but expensive. After selecting my options I end up with a really expensive laptop (EmperorLinux is the same) and for that kind of money you would think I would end up with the highest end components, which I don't. ZaReason is closer but for example, the best vid card it offers is a gtx 670M when I can get a 680M (which is 80 percent faster) from all major high-end winblows retailers like alienware and origin. I can't buy those though if I want to avoid a serious headache. So DIY it is and Ubuntu. :guitar:

---

### Post by Dlambert on 2012-06-12
> **Fait said:**
> Thanks for the links, given that I want to wait until the next LTS before a new purchase I think I'm going to build my own. Just going over it in my head is daunting but: I have a long time to wait, I will learn alot, I get to handpick every part, and I can add in things like A grade thermal paste and heat spreaders; larger capacity fans that are quieter and so on. I've never built a laptop from scratch but I think I'll enjoy the challenge. I'm going to install Ubuntu tonight. I'll give Unity a shot but if I don't like it, I see how much effort it takes to install cinnamon or mate.

System76 - Every laptop seemed to have an HD4000 chip, why? For the money you can spend in upgrades like top of the line core I7, why can I not have even a basic nvidia card?

ZaReason - Is like every other retailer that I like, good but expensive. After selecting my options I end up with a really expensive laptop (EmperorLinux is the same) and for that kind of money you would think I would end up with the highest end components, which I don't. ZaReason is closer but for example, the best vid card it offers is a gtx 670M when I can get a 680M (which is 80 percent faster) from all major high-end winblows retailers like alienware and origin. I can't buy those though if I want to avoid a serious headache. So DIY it is and Ubuntu. :guitar:

No Problem, I'm going to build myself a chimera (Zareason) for college.

---

### Post by Fait on 2012-06-12
HOLY SH*T! Unity got a bit of an upgrade since 11.04. It's hard for me to process exactly how much better this is than that POS back then. I'm sold. I REALLY REALLY like this Unity.
Well thanks all that tried to help. I'll mark this solved tomorrow if no one has any other suggestions, or do you think I can/should repost this in the normal forum now that I'm running Ubuntu?

---

### Post by Fait on 2012-06-12
Well Well Well, now that I have my fancy new Ubuntu installed, I still have the same issues with vlc but smplayer seems to be working properly except that it lags - badly. When I installed it, it said the mplayer version could not be found and asked me to specify, I guess I chose wrong but I don't know how to fix it.

---

### Post by Dlambert on 2012-06-13
> **Fait said:**
> Well Well Well, now that I have my fancy new Ubuntu installed, I still have the same issues with vlc but smplayer seems to be working properly except that it lags - badly. When I installed it, it said the mplayer version could not be found and asked me to specify, I guess I chose wrong but I don't know how to fix it.

In ubuntu, hit "Additional drivers" And see if there are any drivers for your card. (I didn't see if you already had them installed)


If you already have drivers:

Go into terminal and type ```
nvidia-settings
```

And go down to XServer Xvidio settings and Hit Sync to Vsync. Then in OpenGL settings hit sink to Vblank as well. I myself have found turning on All Antialiasing etc to max helps a lot. Also setting the quality to High Quality does wonders as well. 

Anyways, if that doesn't work: Install CCSM (Compiz settings manager) 

```
sudo apt-get install compizconfig-settings-manager
```

Then in general tab, hit vsync.

---

