---
title: "No hibernate option - Linux Mint 15 Cinnamon"
date: 2013-10-10
forum: Any Other OS
---

### Post by bizres on 2013-10-10
Hi,

Since the time I've moved to Linux Mint 15 Cinnamon, I'v never had the hibernate option.

I tried following instructions at [http://www.linuxandlife.com/2012/06/how-to-enable-hibernation-in-linux-mint.html](http://www.linuxandlife.com/2012/06/how-to-enable-hibernation-in-linux-mint.html) but to no avail,even trying to change the Re-enable to enable but with no luck.

I can see there already is a com.ubuntu.enable-hibernate.pkls in /etc/polkit-1/localauthority/50-local.d/
(it's a pkl***s*** not a pkl***a***)

For the record, when I do ***sudo pm-hibernate*** it just makes the system hang.

This is what dconf editor currently shows:
[http://i43.tinypic.com/ndtzec.png](http://i43.tinypic.com/ndtzec.png)

Would really appreciate some help on this, pls.

---

### Post by QIII on 2013-10-10
*Moved to **Other OS/Distro Support***

---

### Post by MIJ-VI on 2013-10-10
> **bizres said:**
> Hi,

Since the time I've moved to Linux Mint 15 Cinnamon, I'v never had the hibernate option.

I tried following instructions at [http://www.linuxandlife.com/2012/06/how-to-enable-hibernation-in-linux-mint.html](http://www.linuxandlife.com/2012/06/how-to-enable-hibernation-in-linux-mint.html) but to no avail,even trying to change the Re-enable to enable but with no luck.

I can see there already is a com.ubuntu.enable-hibernate.pkls in /etc/polkit-1/localauthority/50-local.d/
(it's a pkls not a pkla)

For the record, when I do sudo pm-hibernate it just makes the system hang.

This is what dconf editor currently shows:
[http://i43.tinypic.com/ndtzec.png](http://i43.tinypic.com/ndtzec.png)

Would really appreciate some help on this, pls.

Please help others to help you by supplying more info about your rig:

- In Terminal run **sudo lshw** then post the results in this thread within CODE (#) tags. Doing so will allow us to learn which hardware components your PC is made of.

- IIRC hibernation writes the contents of RAM to a temporary file in the swap partition, thus to facilitate the hibernate function on my machine, I format its hard drive(s) with a swap partition = to the motherboard's maximum amount of installable RAM (to allow for future expansion) + 1 additional GB to ensure said hibernation / temporary file will fit with ease.

---

### Post by bizres on 2013-10-11
> **MIJ-VI said:**
> - In Terminal run **sudo lshw** then post the results in this thread within CODE (#) tags. Doing so will allow us to learn which hardware components your PC is made of.

WOW this is impressive!!

Here's the result:
```
description: Desktop Computer
    product: 10094 (LENOVO_MT_1009)
    vendor: LENOVO
    version: Lenovo H520
    serial: ES11393747
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=desktop family=IdeaCentre keyboard_password=enabled power-on_password=enabled sku=LENOVO_MT_1009 uuid=08BB92E3-A7B7-E211-8E09-EC34C7CC1000
  *-core
       description: Motherboard
       product: MAHOBAY
       vendor: LENOVO
       physical id: 0
       version: NO DPK
       serial: ES11393747
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: ESKT23A
          date: 02/18/2013
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache:0
          description: L2 cache
          physical id: 3e
          slot: CPU Internal L2
          size: 512KiB
          capacity: 512KiB
          capabilities: internal write-through unified
     *-cache:1
          description: L1 cache
          physical id: 3f
          slot: CPU Internal L1
          size: 128KiB
          capacity: 128KiB
          capabilities: internal write-through data
     *-cache:2
          description: L3 cache
          physical id: 40
          slot: CPU Internal L3
          size: 3MiB
          capacity: 3MiB
          capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 41
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: SHARETRONIC
             vendor: 0000
             physical id: 0
             serial: 9F581B05
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             serial: [Empty]
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [Empty]
             slot: ChannelB-DIMM1
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-3220 CPU @ 3.30GHz
          vendor: Intel Corp.
          physical id: 42
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-3220 CPU @ 3.30GHz
          slot: SOCKET 0
          size: 3300MHz
          capacity: 3300MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer xsave avx f16c lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e8000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GF119 [GeForce GT 610]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
           *-multimedia
                description: Audio device
                product: GF119 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7080000-f7083fff
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:43 memory:f710a000-f710a00f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7108000-f71083ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f7100000-f7103fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) ioport:f2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168 PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 09
                serial: 74:27:ea:63:96:df
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-1_0.0.5 06/18/12 ip=192.168.0.107 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7107000-f71073ff
        *-isa
             description: ISA bridge
             product: H61 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7106000-f71067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7105000-f71050ff ioport:f000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600AVJS-6
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WCAV35454993
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000af653
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: cc42de9e-3755-984f-9947-d386849dccb4
                size: 62GiB
                capacity: 62GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-08-12 11:15:28 filesystem=ntfs state=clean
           *-volume:1
                description: EXT3 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1.0
                serial: 6ea573f0-6f57-4b34-b2f8-59e754400a7c
                size: 24GiB
                capacity: 24GiB
                capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2013-02-01 01:39:03 filesystem=ext3 label=tada2 modified=2013-09-20 06:31:23 mounted=2013-09-19 23:21:21 state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 61GiB
                capacity: 61GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 57GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 4052MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM SW820
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 8.41
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500DM002-1BD14
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: KC45
             serial: Z2ASW1KF
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=0005fa54
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /mnt/783EE54307A26E16
                version: 3.1
                serial: 20a9cb7e-e8ea-f141-8d95-736a69878a96
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-03-18 12:00:32 filesystem=ntfs label=tada mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
     *-scsi:3
          physical id: 4
          bus info: usb@2:1.4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=rts5139
        *-disk
             description: SCSI Disk
             product: xD/SD/M.S.
             vendor: Generic-
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 1.00
             serial: 3
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdc
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh

```

---

### Post by MIJ-VI on 2013-10-11
> **bizres said:**
> WOW this is impressive!!

Here's the result:
```
description: Desktop Computer
    product: 10094 (LENOVO_MT_1009)
    vendor: LENOVO
    version: Lenovo H520
    serial: ES11393747
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=desktop family=IdeaCentre keyboard_password=enabled power-on_password=enabled sku=LENOVO_MT_1009 uuid=08BB92E3-A7B7-E211-8E09-EC34C7CC1000
  *-core
       description: Motherboard
       product: MAHOBAY
       vendor: LENOVO
       physical id: 0
       version: NO DPK
       serial: ES11393747
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: ESKT23A
          date: 02/18/2013
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache:0
          description: L2 cache
          physical id: 3e
          slot: CPU Internal L2
          size: 512KiB
          capacity: 512KiB
          capabilities: internal write-through unified
     *-cache:1
          description: L1 cache
          physical id: 3f
          slot: CPU Internal L1
          size: 128KiB
          capacity: 128KiB
          capabilities: internal write-through data
     *-cache:2
          description: L3 cache
          physical id: 40
          slot: CPU Internal L3
          size: 3MiB
          capacity: 3MiB
          capabilities: internal write-back unified
     [B]*-memory
          description: System Memory
          physical id: 41
          slot: System board or motherboard
          size: 4GiB[/B]
        *-bank:0
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: SHARETRONIC
             vendor: 0000
             physical id: 0
             serial: 9F581B05
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             serial: [Empty]
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [Empty]
             slot: ChannelB-DIMM1
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-3220 CPU @ 3.30GHz
          vendor: Intel Corp.
          physical id: 42
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-3220 CPU @ 3.30GHz
          slot: SOCKET 0
          size: 3300MHz
          capacity: 3300MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer xsave avx f16c lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e8000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GF119 [GeForce GT 610]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
           *-multimedia
                description: Audio device
                product: GF119 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7080000-f7083fff
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:43 memory:f710a000-f710a00f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7108000-f71083ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f7100000-f7103fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) ioport:f2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168 PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 09
                serial: 74:27:ea:63:96:df
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-1_0.0.5 06/18/12 ip=192.168.0.107 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7107000-f71073ff
        *-isa
             description: ISA bridge
             product: H61 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7106000-f71067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7105000-f71050ff ioport:f000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600AVJS-6
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WCAV35454993
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000af653
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: cc42de9e-3755-984f-9947-d386849dccb4
                size: 62GiB
                capacity: 62GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-08-12 11:15:28 filesystem=ntfs state=clean
           *-volume:1
                description: EXT3 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1.0
                serial: 6ea573f0-6f57-4b34-b2f8-59e754400a7c
                size: 24GiB
                capacity: 24GiB
                capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2013-02-01 01:39:03 filesystem=ext3 label=tada2 modified=2013-09-20 06:31:23 mounted=2013-09-19 23:21:21 state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 61GiB
                capacity: 61GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 57GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
            [B]  *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 4052MiB[/B]
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM SW820
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 8.41
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500DM002-1BD14
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: KC45
             serial: Z2ASW1KF
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=0005fa54
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /mnt/783EE54307A26E16
                version: 3.1
                serial: 20a9cb7e-e8ea-f141-8d95-736a69878a96
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-03-18 12:00:32 filesystem=ntfs label=tada mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
     *-scsi:3
          physical id: 4
          bus info: usb@2:1.4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=rts5139
        *-disk
             description: SCSI Disk
             product: xD/SD/M.S.
             vendor: Generic-
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 1.00
             serial: 3
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdc
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh

```

Your rig has 4 GB of RAM (4 GB = 4096 MB) and a swap partition of only 4052 MB. <-- This would be the prime suspect IMHO.

Have you ever used another GNU/Linux distro, and if so, has the hibernate function worked with the above hard drives as they are currently partitioned?

The hiberate function has not worked under various versions of Ubuntu on the majority of elderly PCs I've owned over the years but it does work on the two machines I currently own, both of which have hard drives I've manually partitioned (with gparted) to have a swap partition = to 1 GB larger than the maximum amount of RAM the machine can take.

In your case a 5 GB or 5120 MB (1 GB = 1024 MB) swap partition would be worth considering.

Another option would be to create a swap file which resides within an existing ext3/ex4 partion (but I don't know how to do that).

---

### Post by bootch777 on 2014-01-15
Check this topic: [http://ubuntuforums.org/showthread.php?t=2182796](http://ubuntuforums.org/showthread.php?t=2182796) it helped me.

---

### Post by edcompsci on 2014-02-14
I think you should have the pm-hibernate command. If not it's easily installed.



You can use that together with the at command to hibernate at a specified time of day.

To Hibernate at a specified time:

```

sudo at HH:MM

```

You will get an at> prompt:

at>

```

at> pm-hibernate

```
Ctrl+D to leave the at prompt.
You  will get message:
job 1 at (time you specified)

---

