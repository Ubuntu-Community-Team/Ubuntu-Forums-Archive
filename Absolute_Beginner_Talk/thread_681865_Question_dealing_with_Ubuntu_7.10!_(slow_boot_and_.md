---
title: "Question dealing with Ubuntu 7.10! (slow boot and slow after boot)"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Carisma on 2008-01-29
Hello all! First I want to say I just finished installing Ubuntu 7.10 yesterday and I am happy so far, even though I have a couple things I need fixed but the one listed below is my main concern.

1. During boot up my system seems to run really slow and even when Ubuntu is running like there is something running in the background. Would anyone recommend anything to try and increase the boot time and speed up my system.  Boot up takes about 4-5 minutes to fully boot to the login screen and then after I type in my login and password it is another 3-5 minutes for everything to load on the desktop (no icons or anything just the top and bottom bars).

My system:

Ubuntu 7.10 (installed from alternate CD and already updated software)
e2140
GA-P35-DS4
XFX 8600GT
2gb RAM corsair
250gb Seagate

Thanks in advance!

---

### Post by nemilar on 2008-01-29
After you login, go to System - Administration - System Monitor.

There you can see what processes are using the most RAM, CPU, etc.  See if anything sticks out as using up all the resources.  Post the info here, and we can try to help some more.

---

### Post by zero-9376 on 2008-01-29
If it is still slow during normal use maybe you could open the terminal and look at the gnome-system-monitor in system admin to check your cpu usage also have a look in the first tab of system monitor to see what it says about your cpu, maybe its doing power management and throttling your cpu. Have you installed the binary nvidia drivers for your 8600 from restricted driver manager again in the system admin menu?
EDIT: i generally find the system monitor pretty lacking for looking at what process is actually using most cpu you are probably better off looking at the top command in a terminal to identify the process using all your cpu, i recommended system monitor because you can check there whether there IS a process using your cpu and then you could find out specifics from top.

---

### Post by jeffus_il on 2008-01-29
Your system ain't feelin too good.
Could you post the output of dmesg?

---

### Post by Carisma on 2008-01-29
> **nemilar said:**
> After you login, go to System - Administration - System Monitor.

There you can see what processes are using the most RAM, CPU, etc.  See if anything sticks out as using up all the resources.  Post the info here, and we can try to help some more.I will do this when I get home from work in about 2hrs.> **zero-9376 said:**
> If it is still slow during normal use maybe you could open the terminal and look at the gnome-system-monitor in system admin to check your cpu usage also have a look in the first tab of system monitor to see what it says about your cpu, maybe its doing power management and throttling your cpu. Have you installed the binary nvidia drivers for your 8600 from restricted driver manager again in the system admin menu?Yes I installed the nvidia driver.  I remember checking it last night before I went to bed because I did a reboot and when I checked it like right when I got it up and running it was at 50% on each core and I wasn't even doing anything but sitting at the desktop.

---

### Post by Carisma on 2008-01-29
> **jeffus_il said:**
> Your system ain't feelin too good.
Could you post the output of dmesg?Will do that when I get home.

The reason I posted this at work is because I am trying to get ideas to test when I get home since that is the only real free time I have to myself.

---

### Post by Carisma on 2008-01-29
> **jeffus_il said:**
> Your system ain't feelin too good.
Could you post the output of dmesg?

[html][   41.877866] input: Dell Dell USB Mouse as /class/input/input1
[   41.877889] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.2-1
[   41.909831] input: Dell Dell USB Keyboard as /class/input/input2
[   41.909840] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.2-2
[   41.909851] usbcore: registered new interface driver usbhid
[   41.909854] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.963300] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   42.119204] ata1.00: ATAPI: ASUS    DRW-2014L1T, 1.00, max UDMA/66
[   42.274955] ata1.00: configured for UDMA/66
[   42.586304] ata2: SATA link down (SStatus 0 SControl 300)
[   42.586746] scsi 0:0:0:0: CD-ROM            ASUS     DRW-2014L1T      1.00 PQ: 0 ANSI: 5
[   42.588042] ata_piix 0000:00:1f.2: version 2.11
[   42.588049] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   42.588075] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 21
[   42.588104] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   42.588152] scsi2 : ata_piix
[   42.588855] scsi3 : ata_piix
[   42.588960] ata3: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   42.588964] ata4: SATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   42.598118] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   42.598122] Uniform CD-ROM driver Revision: 3.20
[   42.598169] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   42.602203] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   42.770283] ata3.01: Host Protected Area detected:
[   42.770285]  current size: 488395055 sectors
[   42.770286]  native size: 488397168 sectors
[   42.770478] ata3.01: native size increased to 488397168 sectors
[   42.770483] ata3.01: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[   42.770486] ata3.01: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   42.786253] ata3.01: configured for UDMA/133
[   42.949997] ata4.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[   42.950000] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   42.965988] ata4.00: configured for UDMA/133
[   42.966089] scsi 2:0:1:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[   42.966153] scsi 2:0:1:0: Attached scsi generic sg1 type 0
[   42.966232] scsi 3:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[   42.966274] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[   42.966300] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   42.966324] ACPI: PCI Interrupt 0000:00:1f.5[b] -> GSI 19 (level, low) -> IRQ 21
[   42.966351] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   42.966384] scsi4 : ata_piix
[   42.966425] scsi5 : ata_piix
[   42.966521] ata5: SATA max UDMA/133 cmd 0x0001e700 ctl 0x0001e802 bmdma 0x0001eb00 irq 21
[   42.966524] ata6: SATA max UDMA/133 cmd 0x0001e900 ctl 0x0001ea02 bmdma 0x0001eb08 irq 21
[   43.295970] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[   43.295977] ACPI: PCI Interrupt 0000:02:00.1[b] -> GSI 17 (level, low) -> IRQ 17
[   43.296009] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   43.296050] scsi6 : pata_jmicron
[   43.296094] scsi7 : pata_jmicron
[   43.296190] ata7: PATA max UDMA/100 cmd 0x0001c000 ctl 0x0001c102 bmdma 0x0001c400 irq 17
[   43.296195] ata8: PATA max UDMA/100 cmd 0x0001c200 ctl 0x0001c302 bmdma 0x0001c408 irq 17
[   43.304927] sd 2:0:1:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   43.304939] sd 2:0:1:0: [sda] Write Protect is off
[   43.304942] sd 2:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   43.304957] sd 2:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.305010] sd 2:0:1:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   43.305019] sd 2:0:1:0: [sda] Write Protect is off
[   43.305022] sd 2:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   43.305037] sd 2:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.305041]  sda: sda1 sda2 < sda5 >
[   43.344570] sd 2:0:1:0: [sda] Attached SCSI disk
[   43.344625] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   43.344636] sd 3:0:0:0: [sdb] Write Protect is off
[   43.344638] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   43.344653] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.344691] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   43.344701] sd 3:0:0:0: [sdb] Write Protect is off
[   43.344703] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   43.344718] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.344722]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[   43.400404] sd 3:0:0:0: [sdb] Attached SCSI disk
[   43.550504] Attempting manual resume
[   43.550508] swsusp: Resume From Partition 8:5
[   43.550509] PM: Checking swsusp image.
[   43.550666] PM: Resume from disk failed.
[   43.584040] kjournald starting.  Commit interval 5 seconds
[   43.584049] EXT3-fs: mounted filesystem with ordered data mode.
[   51.740405] r8169: eth0: link down
[   52.703996] Linux agpgart interface v0.102 (c) Dave Jones
[   52.841556] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.843176] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   53.214435] input: PC Speaker as /class/input/input3
[   53.399611] parport_pc 00:09: reported by Plug and Play ACPI
[   53.399656] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   53.614413] nvidia: module license 'NVIDIA' taints kernel.
[   53.866617] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   53.866629] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   53.866730] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.09  Fri Jan 11 14:38:28 PST 2008
[   53.934697] NET: Registered protocol family 17
[   54.056511] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   54.056530] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   54.263723] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   54.510341] loop: module loaded
[   54.529387] lp0: using parport0 (interrupt-driven).
[   54.594481] ndiswrapper version 1.45 loaded (smp=yes)
[   54.766516] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[   54.768304] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 19 (level, low) -> IRQ 21
[   54.776462] ndiswrapper: using IRQ 21
[   55.179362] wlan0: ethernet device 00:1a:70:a4:5d:cd using NDIS driver: bcmwl5, version: 0x3642e00, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[   55.179396] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   55.180565] usbcore: registered new interface driver ndiswrapper
[   55.182147] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   55.225106] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
[   55.565190] EXT3 FS on sda1, internal journal
[   56.739698] No dock devices found.
[   56.767831] input: Power Button (FF) as /class/input/input4
[   56.767852] ACPI: Power Button (FF) [PWRF]
[   56.767895] input: Power Button (CM) as /class/input/input5
[   56.767909] ACPI: Power Button (CM) [PWRB]
[   59.538505] ppdev: user-space parallel port driver
[   59.913950] audit(1201571629.273:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5224 profile="/usr/sbin/cupsd"
[   60.030776] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   60.030780] apm: disabled - APM is not SMP safe.
[   62.324300] Failure registering capabilities with primary security module.
[   62.458881] Bluetooth: Core ver 2.11
[   62.458933] NET: Registered protocol family 31
[   62.458935] Bluetooth: HCI device and connection manager initialized
[   62.458939] Bluetooth: HCI socket layer initialized
[   62.465829] Bluetooth: L2CAP ver 2.8
[   62.465833] Bluetooth: L2CAP socket layer initialized
[   62.652392] Bluetooth: RFCOMM socket layer initialized
[   62.652407] Bluetooth: RFCOMM TTY layer initialized
[   62.652409] Bluetooth: RFCOMM ver 1.8
[   95.156050] NET: Registered protocol family 10
[   95.156286] lo: Disabled Privacy Extensions
[   95.156437] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   95.156610] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  127.881200] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  147.527854] eth1: no IPv6 routers present
[  176.992415] kjournald starting.  Commit interval 5 seconds
[  176.992616] EXT3 FS on sdb1, internal journal
[  176.992621] EXT3-fs: mounted filesystem with ordered data mode.
[ 1933.239885] UDF-fs: No VRS found
[ 1933.311591] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1933.428596] ISO 9660 Extensions: RRIP_1991A
[ 2046.498006] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[ 2071.775239] program partprobe is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 2183.082619] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 2183.083166] sd 3:0:0:0: [sdb] Write Protect is off
[ 2183.083169] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 2183.083899] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2183.083903]  sdb: sdb2 sdb3
[ 2185.090873] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 2185.091176] sd 3:0:0:0: [sdb] Write Protect is off
[ 2185.091180] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 2185.091632] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2185.091637]  sdb: sdb2 sdb3
[ 2196.801517] program partprobe is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 2246.709931] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 2261.667366] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 2930.021580] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 3358.293680] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 3526.984680] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 3629.841727] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 3701.481242] kjournald starting.  Commit interval 5 seconds
[ 3701.486409] EXT3 FS on sdb1, internal journal
[ 3701.486524] EXT3-fs: mounted filesystem with ordered data mode.
[ 3943.471079] kjournald starting.  Commit interval 5 seconds
[ 3943.471551] EXT3 FS on sdb2, internal journal
[ 3943.471646] EXT3-fs: mounted filesystem with ordered data mode.
[ 5103.961018] kjournald starting.  Commit interval 5 seconds
[ 5103.961251] EXT3 FS on sdb2, internal journal
[ 5103.961342] EXT3-fs: mounted filesystem with ordered data mode.
[ 5443.360047] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 5655.868390] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 5668.068643] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 5761.393701] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 6201.289075] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 6228.870503] kjournald starting.  Commit interval 5 seconds
[ 6228.877995] EXT3 FS on sdb1, internal journal
[ 6228.878002] EXT3-fs: mounted filesystem with ordered data mode.
[ 6330.268427] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 6342.452061] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 6984.588135] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 6992.955605] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 7062.412669] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 7202.604095] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 7427.255056] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 7531.820064] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 7574.445173] kjournald starting.  Commit interval 5 seconds
[ 7574.449601] EXT3 FS on sdb1, internal journal
[ 7574.449610] EXT3-fs: mounted filesystem with ordered data mode.
[ 7730.891946] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[29848.056928] ndiswrapper: device eth1 removed
[29848.056943] ACPI: PCI interrupt for device 0000:04:01.0 disabled
[29848.057830] usbcore: deregistering interface driver ndiswrapper
[29848.729963] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[29853.866590] PM: suspend-to-disk mode set to 'shutdown'
[29853.866795] swsusp: Basic memory bitmaps created
[29853.866800] Stopping tasks ... done.
[29855.903145] Shrinking memory... done (0 pages freed)
[29855.978339] Freed 0 kbytes in 0.07 seconds (0.00 MB/s)
[29855.978342] Suspending console(s)
[29855.978369] sd 3:0:0:0: [sdb] Synchronizing SCSI cache
[29855.978483] sd 2:0:1:0: [sda] Synchronizing SCSI cache
[29856.178051] usb_device usbdev8.1: PM: suspend 0->1, parent usb8 already 2
[29856.178055] usb_endpoint usbdev8.1_ep81: PM: suspend 0->1, parent 8-0:1.0 already 2
[29856.178058] hub 8-0:1.0: PM: suspend 2->1, parent usb8 already 2
[29856.178061] usb_endpoint usbdev8.1_ep00: PM: suspend 0->1, parent usb8 already 2
[29856.178064] usb_device usbdev7.1: PM: suspend 0->1, parent usb7 already 2
[29856.178067] usb_endpoint usbdev7.1_ep81: PM: suspend 0->1, parent 7-0:1.0 already 2
[29856.178070] hub 7-0:1.0: PM: suspend 2->1, parent usb7 already 2
[29856.178073] usb_endpoint usbdev7.1_ep00: PM: suspend 0->1, parent usb7 already 2
[29856.178092] usb_device usbdev5.1: PM: suspend 0->1, parent usb5 already 2
[29856.178095] usb_endpoint usbdev5.1_ep81: PM: suspend 0->1, parent 5-0:1.0 already 2
[29856.178097] hub 5-0:1.0: PM: suspend 2->1, parent usb5 already 2
[29856.178100] usb_endpoint usbdev5.1_ep00: PM: suspend 0->1, parent usb5 already 2
[29856.178103] usb_device usbdev4.1: PM: suspend 0->1, parent usb4 already 2
[29856.178106] usb_endpoint usbdev4.1_ep81: PM: suspend 0->1, parent 4-0:1.0 already 2
[29856.178109] hub 4-0:1.0: PM: suspend 2->1, parent usb4 already 2
[29856.178111] usb_endpoint usbdev4.1_ep00: PM: suspend 0->1, parent usb4 already 2
[29856.178114] usb_device usbdev3.1: PM: suspend 0->1, parent usb3 already 2
[29856.178117] usb_endpoint usbdev3.1_ep81: PM: suspend 0->1, parent 3-0:1.0 already 2
[29856.178120] hub 3-0:1.0: PM: suspend 2->1, parent usb3 already 2
[29856.178123] usb_endpoint usbdev3.1_ep00: PM: suspend 0->1, parent usb3 already 2
[29856.178126] usb_device usbdev2.1: PM: suspend 0->1, parent usb2 already 2
[29856.178129] usb_endpoint usbdev2.1_ep81: PM: suspend 0->1, parent 2-0:1.0 already 2
[29856.178132] hub 2-0:1.0: PM: suspend 2->1, parent usb2 already 2
[29856.178135] usb_endpoint usbdev2.1_ep00: PM: suspend 0->1, parent usb2 already 2
[29856.178138] usb_device usbdev1.1: PM: suspend 0->1, parent usb1 already 2
[29856.178141] usb_endpoint usbdev1.1_ep81: PM: suspend 0->1, parent 1-0:1.0 already 2
[29856.178143] hub 1-0:1.0: PM: suspend 2->1, parent usb1 already 2
[29856.178146] usb_endpoint usbdev1.1_ep00: PM: suspend 0->1, parent usb1 already 2
[29856.178553] pnp: Device 00:09 disabled.
[29856.178718] pnp: Device 00:08 disabled.
[29856.194600] ACPI: PCI interrupt for device 0000:02:00.1 disabled
[29856.210076] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[29856.210100] NVRM: RmPowerManagement: 3
[29857.671150] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[29857.671694] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[29857.671791] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[29857.687694] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[29857.687730] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[29857.687767] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[29857.691647] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[29857.707654] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
[29857.723634] ACPI: PCI interrupt for device 0000:00:1a.2 disabled
[29857.723670] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
[29857.723707] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
[29857.723760] Disabling non-boot CPUs ...
[29857.839409] CPU 1 is now offline
[29857.839411] SMP alternatives: switching to UP code
[29857.839935] CPU1 is down
[29857.839937] PM: snapshotting memory.
[29857.840103] swsusp: critical section: 
[29857.888109] swsusp: Need to copy 116294 pages
[29857.888112] swsusp: Normal pages needed: 27067 + 1024 + 40, available pages: 202304
[   53.279350] PM: Image restored successfully.
[   53.308451] Enabling non-boot CPUs ...
[   53.640663] SMP alternatives: switching to SMP code
[   53.640822] Booting processor 1/1 eip 3000
[   53.650909] Initializing CPU#1
[   53.728452] Calibrating delay using timer specific routine.. 3199.97 BogoMIPS (lpj=6399956)
[   53.728459] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   53.728465] monitor/mwait feature present.
[   53.728468] CPU: L1 I cache: 32K, L1 D cache: 32K
[   53.728470] CPU: L2 cache: 1024K
[   53.728472] CPU: Physical Processor ID: 0
[   53.728473] CPU: Processor Core ID: 1
[   53.728476] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   53.728925] CPU1: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz stepping 0d
[   53.728941] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   53.749008] CPU1 is up
[   53.749088] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   53.749095] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   53.749142] usb usb1: root hub lost power or was reset
[   53.749158] ACPI: PCI Interrupt 0000:00:1a.1[b] -> GSI 21 (level, low) -> IRQ 18
[   53.749163] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   53.749208] usb usb2: root hub lost power or was reset
[   53.749223] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 19
[   53.749228] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   53.749274] usb usb3: root hub lost power or was reset
[   53.752919] Switched to high resolution mode on CPU 1
[   53.764402] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 19
[   53.764408] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   53.764441] usb usb7: root hub lost power or was reset
[   53.768330] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   53.780396] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100006, writing 100002)
[   53.780410] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   53.780416] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   53.836316] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   53.836353] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   53.836388] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   53.836394] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   53.836399] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   53.836445] usb usb4: root hub lost power or was reset
[   53.836460] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 21
[   53.836465] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   53.836511] usb usb5: root hub lost power or was reset
[   53.836525] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   53.836530] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   53.836576] usb usb6: root hub lost power or was reset
[   53.852260] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   53.852266] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   53.852298] usb usb8: root hub lost power or was reset
[   53.856175] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   53.856210] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   53.856271] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00003, writing 2b00007)
[   53.856284] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 21
[   53.856289] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   53.856340] PM: Writing back config space on device 0000:00:1f.5 at offset 1 (was 2b00003, writing 2b00007)
[   53.856352] ACPI: PCI Interrupt 0000:00:1f.5[b] -> GSI 19 (level, low) -> IRQ 21
[   53.856357] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   53.856399] NVRM: RmPowerManagement: 4
[   54.080903] ata4.00: configured for UDMA/133
[   54.080948] ata3.01: configured for UDMA/133
[   54.080973] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   54.080984] sd 3:0:0:0: [sdb] Write Protect is off
[   54.080986] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   54.081001] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.081019] sd 2:0:1:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   54.081027] sd 2:0:1:0: [sda] Write Protect is off
[   54.081029] sd 2:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   54.081043] sd 2:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.395596] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 100003, writing 100007)
[   54.395621] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   54.395629] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   54.395691] PM: Writing back config space on device 0000:02:00.1 at offset 1 (was 100001, writing 100005)
[   54.395707] ACPI: PCI Interrupt 0000:02:00.1[b] -> GSI 17 (level, low) -> IRQ 17
[   54.395714] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   54.395844] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100007, writing 100003)
[   54.395984] PM: Writing back config space on device 0000:04:01.0 at offset 1 (was 6, writing 2)
[   54.411378] PM: Writing back config space on device 0000:04:06.0 at offset f (was 4020100, writing 4020109)
[   54.411395] PM: Writing back config space on device 0000:04:06.0 at offset 5 (was 0, writing fa100000)
[   54.411400] PM: Writing back config space on device 0000:04:06.0 at offset 4 (was 0, writing fa106000)
[   54.411405] PM: Writing back config space on device 0000:04:06.0 at offset 3 (was 0, writing 2008)
[   54.411412] PM: Writing back config space on device 0000:04:06.0 at offset 1 (was 2100000, writing 2100006)
[   54.460968] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fa106000-fa1067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   54.461606] pnp: Device 00:08 activated.
[   54.462202] pnp: Device 00:09 activated.
[   54.706919] ata2: SATA link down (SStatus 0 SControl 300)
[   54.778798] usb_endpoint usbdev6.2_ep00: PM: resume from 0, parent 6-1 still 1
[   54.778801] usbhid 6-1:1.0: PM: resume from 1, parent 6-1 still 1
[   54.778804] usb_endpoint usbdev6.2_ep81: PM: resume from 0, parent 6-1:1.0 still 1
[   54.778807] usb_device usbdev6.2: PM: resume from 0, parent 6-1 still 1
[   54.778812] usb_endpoint usbdev6.3_ep00: PM: resume from 0, parent 6-2 still 1
[   54.778815] usbhid 6-2:1.0: PM: resume from 1, parent 6-2 still 1
[   54.778817] usb_endpoint usbdev6.3_ep81: PM: resume from 0, parent 6-2:1.0 still 1
[   54.778820] usb_device usbdev6.3: PM: resume from 0, parent 6-2 still 1
[   54.778830] sd 2:0:1:0: [sda] Starting disk
[   54.795052] sd 3:0:0:0: [sdb] Starting disk
[   54.825133] Restarting tasks ... <6>usb 6-1: USB disconnect, address 2
[   54.826724] done.
[   54.826742] swsusp: Basic memory bitmaps freed
[   54.890627] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   54.950530] usb 6-2: USB disconnect, address 3
[   55.202280] ata1.00: configured for UDMA/66
[   55.685348] usb 6-1: new low speed USB device using uhci_hcd and address 4
[   55.858209] usb 6-1: configuration #1 chosen from 1 choice
[   55.876305] input: Dell Dell USB Mouse as /class/input/input6
[   55.876344] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.2-1
[   56.112672] usb 6-2: new low speed USB device using uhci_hcd and address 5
[   56.319489] usb 6-2: configuration #1 chosen from 1 choice
[   56.372542] input: Dell Dell USB Keyboard as /class/input/input7
[   56.372570] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.2-2
[   61.922462] ndiswrapper version 1.45 loaded (smp=yes)
[   61.975332] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[   61.975817] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 19 (level, low) -> IRQ 21
[   61.983290] ndiswrapper: using IRQ 21
[   62.386825] wlan0: ethernet device 00:1a:70:a4:5d:cd using NDIS driver: bcmwl5, version: 0x3642e00, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[   62.386857] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   62.386907] usbcore: registered new interface driver ndiswrapper
[   62.390321] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   62.407383] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   62.413312] r8169 Gigabit Ethernet driver 2.2LK loaded
[   62.413366] PCI: Enabling device 0000:03:00.0 (0000 -> 0003)
[   62.413373] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   62.413393] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   62.414589] eth0: RTL8168b/8111b at 0xf8aa0000, 00:1a:4d:59:4c:c9, XID 38000000 IRQ 17
[   62.470265] r8169: eth0: link down
[   62.472457] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   63.500157] input: Power Button (FF) as /class/input/input8
[   63.500177] ACPI: Power Button (FF) [PWRF]
[   63.500216] input: Power Button (CM) as /class/input/input9
[   63.500229] ACPI: Power Button (CM) [PWRB]
[   64.540681] ACPI: Processor [CPU0] (supports 8 throttling states)
[   64.540731] ACPI: Processor [CPU1] (supports 8 throttling states)
[   64.540741] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   64.540752] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   78.878802] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   93.972441] eth1: no IPv6 routers present[/html]

---

### Post by Carisma on 2008-01-29
> **nemilar said:**
> After you login, go to System - Administration - System Monitor.

There you can see what processes are using the most RAM, CPU, etc.  See if anything sticks out as using up all the resources.  Post the info here, and we can try to help some more.Screenshot is attached

---

### Post by jeffus_il on 2008-01-29
These messages are strange:
>  program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
I can't look at them now, will get back to you. if someone doesn't beat me to it. (that would also be good) Need to get to the root of them as they may be your problem, If you have a chance, google them.

---

### Post by Carisma on 2008-01-29
Here is a bootchart!

---

