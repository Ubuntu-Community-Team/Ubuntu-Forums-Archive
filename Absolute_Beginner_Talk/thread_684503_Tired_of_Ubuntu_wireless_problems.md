---
title: "Tired of Ubuntu wireless problems"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Pulka on 2008-02-01
I´ve been with ubuntu for some years now, and it has been always a nightmare to install wireless networks, or even ADSL. I recently tried PCLinuxOs, and the wireless works very well. What´s wrong in Ubuntu?
I´m giving a last try and asking for your help. Please help me identifying the problem.

**D-link wireless DWL-G510**

**driver=rt61**

**essid hidden**

tried network manager 
tried wifi radar
tried none

**/network/interfaces**

auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp



**iwconfig**

lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.



** ifconfig**

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ra0       Link encap:Ethernet  HWaddr 00:1B:11:BF:63:E1  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24582 (24.0 KB)  TX bytes:0 (0.0 b)
          Interrupt:17 



** lsmod**

Module                  Size  Used by
af_packet              24840  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
sbs                    19592  0 
ac                      6148  0 
dock                   10656  0 
button                  8976  0 
container               5504  0 
video                  18060  0 
battery                11012  0 
sbp2                   24072  0 
lp                     12580  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_hda_intel         263712  0 
snd_emu10k1           137248  1 snd_emu10k1_synth
snd_ac97_codec        100644  1 snd_emu10k1
snd_seq_dummy           4740  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_hda_intel,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            33152  0 
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
emu10k1_gp              4736  0 
gameport               16776  2 emu10k1_gp
atl2                   33304  0 
rt61                  250372  1 
pcspkr                  4224  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
serio_raw               8068  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
xpad                    9988  0 
psmouse                39952  0 
usblp                  15104  0 
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
snd                    54660  14 snd_emux_synth,snd_seq_virmidi,snd_hda_intel,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd_page_alloc         11400  3 snd_hda_intel,snd_emu10k1,snd_pcm
evdev                  11136  4 
ext3                  133896  4 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  9 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
ata_generic             8452  0 
usb_storage            73024  1 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
usbhid                 29536  0 
hid                    28928  1 usbhid
ehci_hcd               36492  0 
floppy                 60004  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_piix               17540  5 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  6 sbp2,sg,sd_mod,sr_mod,usb_storage,libata
uhci_hcd               26640  0 
usbcore               138632  8 xpad,usblp,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


** lshw**

WARNING: you should run this program as super-user.
fields-desktop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1003MB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Ethernet interface
                product: L2 100 Mbit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: a0
                serial: 00:1d:60:29:b6:38
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=ATL2 driverversion=1.0.40.2 firmware=L2 latency=0 module=atl2 multicast=yes
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Wireless interface
                product: RT2561/RT61 rev B 802.11g
                vendor: RaLink
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: ra0
                version: 00
                serial: 00:1b:11:bf:63:e1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt61 latency=64 module=rt61 multicast=yes wireless=RT61 Wireless
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: 1
                bus info: pci@0000:01:01.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-input
                description: Input device controller
                product: SB Audigy Game Port
                vendor: Creative Labs
                physical id: 1.1
                bus info: pci@0000:01:01.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=64 module=emu10k1_gp
           *-firewire
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: 1.2
                bus info: pci@0000:01:01.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom:0
                description: DVD writer
                product: DVD_RW ND-3520A
                vendor: _NEC
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.04
                serial: [_NEC    DVD_RW ND-3520A 1.0404112400
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM TS-H352A
                vendor: TSSTcorp
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: TS03
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-scsi
       physical id: 1
       bus info: scsi@8
       logical name: scsi8
       capabilities: scsi-host
       configuration: driver=usb-storage



** ping 192.168.1.1**
connect: Network is unreachable

** ping 127.0.0.1**
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.032 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.023 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.024 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.022 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.024 ms

---

### Post by Golem XIV on 2008-02-01
Have you tried [this]("http://ubuntuforums.org/showthread.php?t=202834&highlight=G510"), [this]("http://ubuntuforums.org/showthread.php?t=669222&highlight=G510"), [this]("http://ubuntuforums.org/showthread.php?t=654940&highlight=G510"), [this]("http://ubuntuforums.org/showthread.php?t=132980&highlight=G510") or [this]("http://ubuntuforums.org/showthread.php?t=647441&highlight=G510")?  Most claim to have solved the problem with that same wireless device.

---

