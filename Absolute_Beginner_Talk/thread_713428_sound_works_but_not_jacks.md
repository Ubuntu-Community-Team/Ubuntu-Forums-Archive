---
title: "sound works but not jacks"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-02
My sound work fine but when i plug in my headphone jacks sound still comes out the the speakers in my laptop.

---

### Post by julian67 on 2008-03-02
> **RyanZec said:**
> My sound work fine but when i plug in my headphone jacks sound still comes out the the speakers in my laptop.

This is a very common problem, particularly with intel-hda sound controllers. You'll need to post your laptop model and ideally audio hardware specs. I don't know if the tool lshw is included by default but if you have it then do ```
sudo lshw
``` and post the output of anything to do with sound or audio or multimedia. Or use ```
lspci | grep audio
``` and post that output.

---

### Post by LuisGMarine on 2008-03-02
I have the same problem, going to stick around this thread to see if we can find a fix that will help many users having trouble!

---

### Post by julian67 on 2008-03-03
> **LuisGMarine said:**
> I have the same problem, going to stick around this thread to see if we can find a fix that will help many users having trouble!

It's a common problem, if you know your laptop model and hardware you can possibly find a solution more easily by searching the forum. If it's an intel-hda sound controller you might find some help here [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")

---

### Post by RyanZec on 2008-03-04
lshw output:

ryanzec-laptop            
    description: Notebook
    product: GX700
    vendor: Micro-Star International
    version: Ver 1.000
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: MS-1719x
       vendor: MSI
       physical id: 0
       version: Ver 1.000
       serial: BSS-0123456789
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080014 (07/26/2007)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int17printer acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2201MHz
          capacity: 2201MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KB
             capacity: 64KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MB
             capacity: 4MB
             capabilities: internal write-back instruction
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: SODIMM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GB
             width: 64 bits
        *-bank:1
             description: SODIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: SODIMM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600M GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Contoller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth1
                version: 02
                serial: 00:1b:77:90:92:94
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () ip=192.168.1.3 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
        *-pci:5
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 01
                serial: 00:19:db:ea:7e:76
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 module=ohci1394
           *-system
                description: Generic system peripheral
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 4.2
                bus info: pci@0000:01:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 4.3
                bus info: pci@0000:01:04.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm cap_list
                configuration: latency=64
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7530B
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: NX02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: SCSI Disk
                product: Hitachi HTS54252
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BBFO
                serial: 070812BB0F00WDG030HA
                size: 232GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 227GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5898MB
                   capacity: 5898MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5898MB
                      capabilities: nofs
     *-scsi
          physical id: 1
          bus info: usb@1:3.1
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB SD Reader
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: USB CF Reader
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@3:0.0.1
             logical name: /dev/sdc
             version: 1.01
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: USB SM Reader
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@3:0.0.2
             logical name: /dev/sdd
             version: 1.02
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: USB MS Reader
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@3:0.0.3
             logical name: /dev/sde
             version: 1.03
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sde

lspci | grep audio output nothing.  I have tried follow some of the howto but still can not get headphones or mic working.

---

### Post by julian67 on 2008-03-05
OK the important information is that your laptop is an MSI GX700 with an Intel ICH8 HD Audio sound controller. From what I understand this sound controller is not properly supported in default Gutsy but is supported by a backport, so what you need to do is start Synaptic>Settings>Repositories>Updates and check the box for Gutsy Backports, then reload as prompted. Then install linux-backports-modules-generic. This will install (amongst other things) a newer version of ALSA (Advanced Linux Sound Architecture). When it's done you should find there are a lot more settings for your sound card in the sound mixer and you should be able to get everything set up the way you like (if it doesn't work right away). Good luck!

---

### Post by RyanZec on 2008-03-05
I have installed the modules but sounds still play from my laptop speakers and my headphones when i plug them in.  I don't see any option in the sound configuration that would effect this.

---

### Post by julian67 on 2008-03-05
ok try this command to find out some more about your sound system ```
cat /proc/asound/card0/codec#* | grep Codec
```

It should give you some output ```
Codec: your_codec_here
```

Then have a look at the following list and hopefully you'll find your codec listed and also a hardware description similar to or exactly the same as on your laptop: 

For example if I found my laptop has ALC880 codec (the 1st one in this list) and I can see it has 5 audio jacks rear and 2 front I'd edit the file /etc/modprobe.d/alsa-base and add the line ```
options snd-hda-intel model=5stack
``` and then reboot and hopefully it would all be ready to go. There's no guarantees though, some combinations of hardware are going to be more difficult than others, some might never be satisfactory. Other places you can look for help would be [https://wiki.ubuntu.com/LaptopTestingTeam/MSI]("https://wiki.ubuntu.com/LaptopTestingTeam/MSI")

>   Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
        ATI SB450, SB600, RS600,
        VIA VT8251/VT8237A,
        SIS966, ULI M5461

    model    - force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size)
    probe_mask  - Bitmask to probe codecs (default = -1, meaning all slots)
    single_cmd  - Use single immediate commands to communicate with
        codecs (for debugging only)
    enable_msi    - Enable Message Signaled Interrupt (MSI) (default = off)

    This module supports one card and autoprobe.

    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

      Model name    Description
      ----------    -----------
    ALC880
      3stack    3-jack in back and a headphone out
      3stack-digout    3-jack in back, a HP out and a SPDIF out
      5stack    5-jack in back, 2-jack in front
      5stack-digout    5-jack in back, 2-jack in front, a SPDIF out
      6stack    6-jack in back, 2-jack in front
      6stack-digout    6-jack with a SPDIF out
      w810        3-jack
      z71v        3-jack (HP shared SPDIF)
      asus        3-jack (ASUS Mobo)
      asus-w1v    ASUS W1V
      asus-dig    ASUS with SPDIF out
      asus-dig2    ASUS with SPDIF out (using GPIO2)
      uniwill    3-jack
      fujitsu    Fujitsu Laptops (Pi1536)
      F1734        2-jack
      lg        LG laptop (m1 express dual)
      lg-lw        LG LW20/LW25 laptop
      tcl        TCL S700
      clevo        Clevo laptops (m520G, m665n)
      test        for testing/debugging purpose, almost all controls can be
            adjusted.  Appearing only when compiled with
            $CONFIG_SND_DEBUG=y
      auto        auto-config reading BIOS (default)

    ALC260
      hp        HP machines
      hp-3013    HP machines (3013-variant)
      fujitsu    Fujitsu S7020
      acer        Acer TravelMate
      basic        fixed pin assignment (old default model)
      auto        auto-config reading BIOS (default)

    ALC262
      fujitsu    Fujitsu Laptop
      hp-bpc    HP xw4400/6400/8400/9400 laptops
      hp-bpc-d7000    HP BPC D7000
      benq        Benq ED8
      hippo        Hippo (ATI) with jack detection, Sony UX-90s
      hippo_1    Hippo (Benq) with jack detection
      basic        fixed pin assignment w/o SPDIF
      auto        auto-config reading BIOS (default)

    ALC882/885
      3stack-dig    3-jack with SPDIF I/O
      6stack-dig    6-jack digital with SPDIF I/O
      arima        Arima W820Di1
      macpro    MacPro support
      w2jc        ASUS W2JC
      auto        auto-config reading BIOS (default)

    ALC883/888
      3stack-dig    3-jack with SPDIF I/O
      6stack-dig    6-jack digital with SPDIF I/O
      3stack-6ch    3-jack 6-channel
      3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
      6stack-dig-demo  6-jack digital for Intel demo board
      acer        Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
      medion    Medion Laptops
      targa-dig    Targa/MSI
      targa-2ch-dig    Targs/MSI with 2-channel
      laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
      auto        auto-config reading BIOS (default)

    ALC861/660
      3stack    3-jack
      3stack-dig    3-jack with SPDIF I/O
      6stack-dig    6-jack with SPDIF I/O
      3stack-660    3-jack (for ALC660)
      uniwill-m31    Uniwill M31 laptop
      toshiba    Toshiba laptop support
      asus        Asus laptop support
      asus-laptop    ASUS F2/F3 laptops
      auto        auto-config reading BIOS (default)

    ALC861VD/660VD
      3stack    3-jack
      3stack-dig    3-jack with SPDIF OUT
      6stack-dig    6-jack with SPDIF OUT
      3stack-660    3-jack (for ALC660VD)
      lenovo    Lenovo 3000 C200
      auto        auto-config reading BIOS (default)

    CMI9880
      minimal    3-jack in back
      min_fp    3-jack in back, 2-jack in front
      full        6-jack in back, 2-jack in front
      full_dig    6-jack in back, 2-jack in front, SPDIF I/O
      allout    5-jack in back, 2-jack in front, SPDIF out
      auto        auto-config reading BIOS (default)

    AD1884
      N/A

    AD1981
      basic        3-jack (default)
      hp        HP nx6320
      thinkpad    Lenovo Thinkpad T60/X60/Z60
      toshiba    Toshiba U205

    AD1983
      N/A

    AD1984
      basic        default configuration
      thinkpad    Lenovo Thinkpad T61/X61

    AD1986A
      6stack    6-jack, separate surrounds (default)
      3stack    3-stack, shared surrounds
      laptop    2-channel only (FSC V2060, Samsung M50)
      laptop-eapd    2-channel with EAPD (Samsung R65, ASUS A6J)
      ultra        2-channel with EAPD (Samsung Ultra tablet PC)

    AD1988
      6stack    6-jack
      6stack-dig    ditto with SPDIF
      3stack    3-jack
      3stack-dig    ditto with SPDIF
      laptop    3-jack with hp-jack automute
      laptop-dig    ditto with SPDIF
      auto        auto-config reading BIOS (default)
    
    Conexant 5045
      laptop    Laptop config 
      test        for testing/debugging purpose, almost all controls
            can be adjusted.  Appearing only when compiled with
            $CONFIG_SND_DEBUG=y

    Conexant 5047
      laptop    Basic Laptop config 
      laptop-hp    Laptop config for some HP models (subdevice 30A5)
      laptop-eapd    Laptop config with EAPD support
      test        for testing/debugging purpose, almost all controls
            can be adjusted.  Appearing only when compiled with
            $CONFIG_SND_DEBUG=y

    STAC9200/9205/9254
      ref        Reference board

    STAC9220/9221
      ref        Reference board
      3stack    D945 3stack
      5stack    D945 5stack + SPDIF
      intel-mac-v1    Intel Mac Type 1
      intel-mac-v2    Intel Mac Type 2
      intel-mac-v3    Intel Mac Type 3
      intel-mac-v4    Intel Mac Type 4
      intel-mac-v5    Intel Mac Type 5
      macmini    Intel Mac Mini (equivalent with type 3)
      macbook    Intel Mac Book (eq. type 5)
      macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
      macbook-pro    Intel Mac Book Pro 2nd generation (eq. type 3)
      imac-intel    Intel iMac (eq. type 2)
      imac-intel-20    Intel iMac (newer version) (eq. type 3)

    STAC9202/9250/9251
      ref        Reference board, base config
      m2-2        Some Gateway MX series laptops
      m6        Some Gateway NX series laptops
      pa6        Gateway NX860 series

    STAC9227/9228/9229/927x
      ref        Reference board
      3stack    D965 3stack
      5stack    D965 5stack + SPDIF

    STAC9872
      vaio        Setup for VAIO FE550G/SZ110
      vaio-ar Setup for VAIO AR

    The model name "genric" is treated as a special case.  When this
    model is given, the driver uses the generic codec parser without
    "codec-patch".  It's sometimes good for testing and debugging.

    If the default configuration doesn't work and one of the above
    matches with your device, report it together with the PCI
    subsystem ID (output of "lspci -nv") to ALSA BTS or alsa-devel
    ML (see the section "Links and Addresses").

    Note 2: If you get click noises on output, try the module option
        position_fix=1 or 2.  position_fix=1 will use the SD_LPIB
        register value without FIFO size correction as the current
        DMA pointer.  position_fix=2 will make the driver to use
        the position buffer instead of reading SD_LPIB register.
        (Usually SD_LPLIB register is more accurate than the
        position buffer.)

    NB: If you get many "azx_get_response timeout" messages at
    loading, it's likely a problem of interrupts (e.g. ACPI irq
    routing).  Try to boot with options like "pci=noacpi".  Also, you
    can try "single_cmd=1" module option.  This will switch the
    communication method between HDA controller and codecs to the
    single immediate commands instead of CORB/RIRB.  Basically, the
    single command mode is provided only for BIOS, and you won't get
    unsolicited events, too.  But, at least, this works independently
    from the irq.  Remember this is a last resort, and should be
    avoided as much as possible...
    
    MORE NOTES ON "azx_get_response timeout" PROBLEMS:
    On some hardwares, you may need to add a proper probe_mask option
    to avoid the "azx_get_response timeout" problem above, instead.
    This occurs when the access to non-existing or non-working codec slot
    (likely a modem one) causes a stall of the communication via HD-audio
    bus.  You can see which codec slots are probed by enabling
    CONFIG_SND_DEBUG_DETECT, or simply from the file name of the codec
    proc files.  Then limit the slots to probe by probe_mask option.
    For example, probe_mask=1 means to probe only the first slot, and
    probe_mask=4 means only the third slot.

    The power-management is supported.

---

### Post by wieman01 on 2008-03-05
I had the same issue with a intel-hda sound controller. It turned out it was muted by default and I simply had to turn on the sound. You can do so using the sound panel or alsamixer:
> alsamixer
That was also on Feisty.

---

### Post by RyanZec on 2008-03-05
> **wieman01 said:**
> I had the same issue with a intel-hda sound controller. It turned out it was muted by default and I simply had to turn on the sound. You can do so using the sound panel or alsamixer:

That was also on Feisty.

I am not quite sure if you understand my issue.  The sound works fine on my laptop speaker and it also works fine on my headphones, the issue is when I plug-in my headphones I get sound from my headphones AND laptop speaker.  Is this how you understand my problem?

---

### Post by RyanZec on 2008-03-05
I have the ALC888 and still can not get only the headphones to work, both still play when headphones are pluged in.

---

### Post by RyanZec on 2008-03-05
does it have anything to do with that i am running the 64-bit OS?

---

### Post by wieman01 on 2008-03-05
> **RyanZec said:**
> I am not quite sure if you understand my issue.  The sound works fine on my laptop speaker and it also works fine on my headphones, the issue is when I plug-in my headphones I get sound from my headphones AND laptop speaker.  Is this how you understand my problem?
Oops, yes, you are right. I did not quite get it... Just ignore my last post.

---

### Post by julian67 on 2008-03-05
don't know, have no experience of 64 bit, but I'd guess it's not relevant as ALSA should be the same 32 or 64 bit. You might want to try compiling hte latest version of ALSA.

---

