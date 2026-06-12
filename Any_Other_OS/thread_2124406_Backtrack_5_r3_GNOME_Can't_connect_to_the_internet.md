---
title: "Backtrack 5 r3 GNOME Can't connect to the internet with TP-Link TL-WN722N card"
date: 2013-03-10
forum: Any Other OS
---

### Post by TomGauss on 2013-03-10
Hi, I am new to this forum and to linux, so if I post with bad etiquette or anything, I apologize.

Alright, here is my problem. I am running Backtrack 5 r3 fully installed  on my hdd, with a TP-link TL-WN722N USB wireless card. I know that  Backtrack detects my device because it shows up as 'Atheros AR9271' (I shortened that name a little but I will post the results of lsusb below which has the full name) when  I run lsusb. However, when I open wicd, it shows that there are no  networks available. Here are some ideas I've had: 
1) I have the AR9271 driver, but I don't know if it's installed or not (it may be installed by default but I am not sure). 
2) It may have something to do with me needing to do a modeswitch. I tried usb_modeswitch -v 0cf3 -p 9271 but didn't seem to have any luck with it (I will post the result of that below). 
3) My wireless interface file seems to be lacking something, but I am not sure what (I will post its contents below), and if it is, I am not sure what to do with it. 
4) The wireless card is a USB 2.0 device (as are my mouse and keyboard),  and when I am on Windows the wireless card won't work in a USB 3.0 port.  However, when I am on backtrack none of the USB 2.0 ports work; it  doesn't recognize my mouse, keyboard, or wireless card unless they are  plugged into one of the USB 3.0 ports. So I am thinking this whole thing could  have something to do with the level of compatibility my wireless card  has with USB 3.0. I know nothing about that, though.

Here are the results of a few commands: 

lsmod

```

root@bt:~# lsmod
Module                  Size  Used by
ath9k                 134009  0 
ath9k_htc              91070  0 
mac80211              478885  2 ath9k,ath9k_htc
ath9k_common           13604  2 ath9k,ath9k_htc
ath9k_hw              401846  3 ath9k,ath9k_htc,ath9k_common
ath                    22992  4 ath9k,ath9k_htc,ath9k_common,ath9k_hw
cfg80211              190023  4 ath9k,ath9k_htc,mac80211,ath
dm_crypt               22668  0 
joydev                 17457  0 
snd_hda_codec_hdmi     31994  0 
usbhid                 46275  0 
hid                    97618  1 usbhid
snd_hda_codec_realtek   222503  1 
snd_hda_intel          33175  0 
snd_hda_codec         110336  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13554  1 snd_hda_codec
snd_pcm                92879  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            29179  1 snd_seq_midi
snd_seq_midi_event     14436  1 snd_seq_midi
snd_seq                60549  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28838  2 snd_pcm,snd_seq
snd_seq_device         14129  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64384  10 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12598  1 snd
snd_page_alloc         18101  2 snd_hda_intel,snd_pcm
psmouse                72820  0 
sp5100_tco             13697  0 
lp                     17789  0 
parport                44368  1 lp
serio_raw              13211  0 
edac_core              51499  0 
edac_mce_amd           22882  0 
i2c_piix4              13167  0 
k10temp                13119  0 
fam15h_power           12985  0 
dm_mirror              21906  0 
dm_region_hash         19667  1 dm_mirror
dm_log                 18215  2 dm_mirror,dm_region_hash
aufs                  183689  0 
mxm_wmi                12823  0 
r8169                  56455  0 
pata_atiixp            13168  0 
wmi                    18697  1 mxm_wmi

```

lsusb -s 010:003 -v

```

root@bt:~# lsusb -s 010:003 -v

Bus 010 Device 003: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0cf3 Atheros Communications, Inc.
  idProduct          0x9271 AR9271 802.11n
  bcdDevice            1.08
  iManufacturer          16 ATHEROS
  iProduct               32 USB2.0 WLAN
  iSerial                48 12345
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           60
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```


usb_modeswitch -v 0cf3 -p 9271

```


root@bt:~# usb_modeswitch -v 0cf3 -p 9271  Looking for default devices ...  Found devices in default mode or class (1) Accessing device 003 on bus 010 ... Using endpoints 0x01 (out) and 0x82 (in) Not a storage device, skipping SCSI inquiry  USB description data (for identification) ------------------------- Manufacturer: ATHEROS      Product: USB2.0 WLAN   Serial No.: 12345 ------------------------- Warning: no switching method given. -> Run lsusb to note any changes. Bye

```


iwconfig

```

root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



```

ifconfig

```

root@bt:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 94:de:80:21:35:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:75 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7489 (7.4 KB)  TX bytes:7489 (7.4 KB)

```

airmon-ng

```

root@bt:~# airmon-ng


Interface    Chipset        Driver



```

lshw

```

root@bt:~# lshw
bt                        
    description: Desktop Computer
    product: To be filled by O.E.M.
    vendor: Gigabyte Technology Co., Ltd.
    version: To be filled by O.E.M.
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop uuid=9402DE03-8004-2105-3506-CE0700080009
  *-core
       description: Motherboard
       product: 990FXA-UD3
       vendor: AMD Corporation
       physical id: 0
       version: x.x
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: FA (10/23/2012)
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: AMD FX(tm)-8350 Eight-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD FX(tm)-8350 Eight-Core Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1400MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr tbm topoext perfctr_core arat cpb npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 384KiB
             capacity: 384KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Dimm0_PartNum
             vendor: Dimm0_Manufacturer
             physical id: 0
             serial: Dimm0_SerNum
             slot: Node0_Dimm0
        *-bank:1
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: F3-1600C9-8GX
             vendor: Undefined
             physical id: 1
             serial: 00000000
             slot: Node0_Dimm1
             size: 8GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM Synchronous [empty]
             product: Dimm2_PartNum
             vendor: Dimm2_Manufacturer
             physical id: 2
             serial: Dimm2_SerNum
             slot: Node0_Dimm2
        *-bank:3
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: F3-1600C9-8GX
             vendor: Undefined
             physical id: 3
             serial: 00000000
             slot: Node0_Dimm3
             size: 8GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: RD890 PCI to PCI bridge (external gfx0 port B)
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port B)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52 ioport:e000(size=4096) memory:fea00000-feafffff ioport:c0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff memory:fea00000-fea3ffff ioport:e000(size=256) memory:fea40000-fea5ffff
           *-multimedia UNCLAIMED
                description: Audio device
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:fea60000-fea63fff
        *-pci:1
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port H)
             vendor: ATI Technologies Inc
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:53 memory:fe900000-fe9fffff
           *-usb
                description: USB Controller
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:73 memory:fe900000-fe907fff
        *-pci:2
             description: PCI bridge
             product: RD890 PCI to PCI bridge (external gfx1 port A)
             vendor: ATI Technologies Inc
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:54 ioport:d000(size=4096) memory:fe800000-fe8fffff
           *-storage
                description: SATA controller
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:72 ioport:d040(size=8) ioport:d030(size=4) ioport:d020(size=8) ioport:d010(size=4) ioport:d000(size=16) memory:fe810000-fe8101ff memory:fe800000-fe80ffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:feb0b000-feb0b3ff
           *-disk:0
                description: ATA Disk
                product: ST31000524AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: JC4B
                serial: 5VPDER7B
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9086336c
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/System Reserved
                   version: 3.1
                   serial: 32a2-d000
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-01-02 21:35:07 filesystem=ntfs label=System Reserved mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/2656A4B456A485E1
                   version: 3.1
                   serial: 7225ee2b-973e-0343-9f5b-0ee9647d92d6
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-01-02 21:35:08 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-disk:1
                description: ATA Disk
                product: ST31000524AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: JC4B
                serial: 5VPDD78B
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000a79c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: fc0a9244-0bec-4924-b596-49362f1e6cf1
                   size: 893GiB
                   capacity: 893GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2013-02-25 06:15:10 filesystem=ext4 lastmountpoint=/arget modified=2013-02-25 06:35:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2013-03-10 17:09:39 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 37GiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb0a000-feb0afff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb09000-feb090ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb08000-feb08fff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb07000-feb070ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi6
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DRW-24B1ST   c
                vendor: ASUS
                physical id: 0.0.0
                bus info: scsi@6:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb00000-feb03fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master vga_palette
             resources: ioport:c000(size=4096) memory:fe700000-fe7fffff
           *-firewire UNCLAIMED
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: e
                bus info: pci@0000:04:0e.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=32
                resources: memory:fe700000-fe7007ff ioport:c000(size=128)
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb06000-feb06fff
        *-pci:4
             description: PCI bridge
             product: SB700/SB800 PCI to PCI bridge (PCIE port 0)
             vendor: ATI Technologies Inc
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:b000(size=4096) ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 06
                serial: 94:de:80:21:35:ce
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-3.fw latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:75 ioport:b000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
        *-pci:5
             description: PCI bridge
             product: SB700/SB800 PCI to PCI bridge (PCIE port 1)
             vendor: ATI Technologies Inc
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:fe600000-fe6fffff
           *-usb
                description: USB Controller
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:74 memory:fe600000-fe607fff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb05000-feb05fff
        *-usb:6
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb04000-feb040ff
     *-pci:1
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz

```

and finally the contents of my network interface file

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```


So that was probably a bit too much information, but I thought I'd err on the side of caution. 
Thanks in advance to anyone who reads this, or to anyone who can help me!

---

### Post by trh51 on 2013-03-11
I had the same problem. Backtrack recognizes it but it does not have the driver.

If its on a Live CD then boot up with a physical connection so you can download the drivers automatically or if its installed on the HDD then you want to Google installing (or activating) the specific driver.

---

### Post by TomGauss on 2013-03-11
> **trh51 said:**
> I had the same problem. Backtrack recognizes it but it does not have the driver.

If its on a Live CD then boot up with a physical connection so you can download the drivers automatically or if its installed on the HDD then you want to Google installing (or activating) the specific driver.

Thanks for the help! I found something that looks promising, but I haven't gotten the chance to try it. I will post back here again when I have tried it and let you know whether it worked or not.

---

### Post by TomGauss on 2013-03-11
Alright, so I got the compat wireless drivers from here: [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/compat-drivers/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/compat-drivers/)
 and ran 

```


tar -xf /root/compat-drivers-3.9-rc2-2-su.tar.bz2 
cd compat-drivers-3.9-rc2-2-su 
make 
make install 
make unload 
reboot

```

which ran through all of the install info. Then I ran a modprobe for two of the ath9k drivers

```

modprobe ath9k_htc
modprobe ath9k


```

but nothing happened. I don't know if this is whats supposed to happen if everything is running smoothly or not. 
Then I rebooted, and ran service networking start, and service wicd start, but when I opened wicd there were no connections available. 
and when I run airmon-ng it still doesn't recognize my device. It just gives the same output I posted above when I ran it before. 

What am I doing wrong?

---

### Post by QIII on 2013-03-11
*Moved to **Other OS/Distro Talk***

Although Bactrack is based on Ubuntu, it is a customized distro in its own right.

I suggest the following as a good resource:

[http://www.backtrack-linux.org/forums](http://www.backtrack-linux.org/forums)

---

### Post by TomGauss on 2013-03-11
Thanks for the correction, and for the suggestion. I did try posting there as well before I came here, but only one person replied with a suggestion, which I tried but it didn't work for me.

---

