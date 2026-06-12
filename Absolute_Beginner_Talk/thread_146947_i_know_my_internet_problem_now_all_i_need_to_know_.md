---
title: "i know my internet problem now all i need to know is where i can get drivers"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by katarot on 2006-03-19
i have been trying to get internet on my dell inspiron 1300 for days now 
and last night i came across a thread in the forums and there was alot of people having the same problem as me it is something dell does so that the wireless card only swicthes on when windows xp starts up

i need to know if there is another place i can get the bcmwl5.inf and .sys
and work with ndiswrapper 

that worked with most of the people in that thread 
please help me on this i feel so close now

---

### Post by fimbulvetr on 2006-03-19
I recall hearing about this. I also recall someone saying that the drivers from HP/Compaq worked. Try finding a HP/Compaq that has the same card, and using the drivers for it.

---

### Post by katarot on 2006-03-19
the hp ones dont work 
i have tried linksys and acer they install fine but the hardware is not there 
i know i use broadcom 4318 
can any one recommend  one 
i know it should work if i got the hardware because when i installed these drivers
they were different from the ones i got from dell so it is working 
i just need one that uses the same hardware

---

### Post by katarot on 2006-03-19
ever one i have installed apart from linksys have found 
hardware present 
device present 
but when i go to system > administration > networks there is nothing new there
why is this not working it has work for people who have practically the same laptop only a different version 
has any one else having the same problem with dell inspiron 1300 or other dell
any one had any success i feel like there is no more i can do here i have tried everything 
nothing seems to be working 
arghh i really need help and loads of it

---

### Post by fimbulvetr on 2006-03-19
Go to cmd line and type:

```

dmesg

```

Paste the output here. Make sure turn on ndiswrapper and stuff before you do the dmesg.

---

### Post by katarot on 2006-03-19
here is what i got 

martin@ubuntu:~$ dmesg
sk quotas dquot_6.5.1
[4294669.702000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.702000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.702000] devfs: boot_options: 0x0
[4294669.702000] Initializing Cryptographic API
[4294669.702000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294669.702000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294669.702000] assign_interrupt_mode Found MSI capability
[4294669.702000] Allocate Port Service[pcie00]
[4294669.702000] Allocate Port Service[pcie02]
[4294669.702000] Allocate Port Service[pcie03]
[4294669.702000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[4294669.702000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[4294669.702000] assign_interrupt_mode Found MSI capability
[4294669.702000] Allocate Port Service[pcie00]
[4294669.702000] Allocate Port Service[pcie02]
[4294669.702000] Allocate Port Service[pcie03]
[4294669.702000] isapnp: Scanning for PnP cards...
[4294670.054000] isapnp: No Plug & Play device found
[4294670.072000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294670.072000] i8042.c: Warning: Keylock active.
[4294670.073000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.073000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.073000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294670.076000] io scheduler noop registered
[4294670.076000] io scheduler anticipatory registered
[4294670.076000] io scheduler deadline registered
[4294670.076000] io scheduler cfq registered
[4294670.076000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.077000] EISA: Probing bus 0 at eisa.0
[4294670.077000] Cannot allocate resource for EISA slot 1
[4294670.077000] EISA: Detected 0 cards.
[4294670.077000] NET: Registered protocol family 2
[4294670.081000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.087000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294670.087000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[4294670.087000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294670.087000] TCP: Hash tables configured (established 8192 bind 8192)
[4294670.087000] NET: Registered protocol family 8
[4294670.087000] NET: Registered protocol family 20
[4294670.087000] ACPI wakeup devices:
[4294670.087000]  LID PBTN PCI0 USB0 USB1 USB2 USB4 USB3 AZAL MODM PCIE RP01 RP02 RP03 RP04 RP05 RP06
[4294670.087000] ACPI: (supports S0 S3 S4 S4bios S5)
[4294670.087000] Freeing unused kernel memory: 224k freed
[4294670.100000] vga16fb: initializing
[4294670.100000] vga16fb: mapped to 0xc00a0000
[4294670.241000] Console: switching to colour frame buffer device 80x30
[4294670.241000] fb0: VGA16 VGA frame buffer device
[4294671.371000] Capability LSM initialized
[4294671.381000] NET: Registered protocol family 1
[4294671.397000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.397000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.397000] ACPI: bus type ide registered
[4294671.400000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294671.400000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[4294671.400000] ICH6: chipset revision 3
[4294671.400000] ICH6: not 100% native mode: will probe irqs later
[4294671.400000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:DMA
[4294671.400000] Probing IDE interface ide0...
[4294671.664000] hda: FUJITSU MHV2040AH, ATA DISK drive
[4294672.072000] hdb: TSSTcorpCD-RW/DVD-ROM TSL462C, ATAPI CD/DVD-ROM drive
[4294672.377000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.378000] Probing IDE interface ide1...
[4294672.891000] Probing IDE interface ide2...
[4294673.403000] Probing IDE interface ide3...
[4294673.915000] Probing IDE interface ide4...
[4294674.427000] Probing IDE interface ide5...
[4294674.942000] hda: max request size: 128KiB
[4294675.016000] hda: 78140160 sectors (40007 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[4294675.021000] hda: cache flushes supported
[4294675.021000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4
[4294675.076000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 1536kB Cache
[4294675.076000] Uniform CD-ROM driver Revision: 3.20
[4294675.295000] Attempting manual resume
[4294675.295000] swsusp: Suspend partition has wrong signature?
[4294675.351000] usbcore: registered new driver usbfs
[4294675.351000] usbcore: registered new driver hub
[4294675.352000] USB Universal Host Controller Interface driver v2.2
[4294675.352000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294675.352000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294675.352000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294675.414000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294675.414000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[4294675.414000] hub 1-0:1.0: USB hub found
[4294675.414000] hub 1-0:1.0: 2 ports detected
[4294675.417000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[4294675.417000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.417000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294675.479000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294675.479000] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[4294675.479000] hub 2-0:1.0: USB hub found
[4294675.479000] hub 2-0:1.0: 2 ports detected
[4294675.482000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294675.482000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294675.482000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294675.544000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294675.544000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[4294675.544000] hub 3-0:1.0: USB hub found
[4294675.544000] hub 3-0:1.0: 2 ports detected
[4294675.547000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[4294675.547000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294675.547000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294675.583000] usb 1-1: new full speed USB device using uhci_hcd and address 2[4294675.609000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294675.609000] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[4294675.609000] hub 4-0:1.0: USB hub found
[4294675.609000] hub 4-0:1.0: 2 ports detected
[4294675.644000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
[4294675.644000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.644000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294675.644000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.644000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294675.644000] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xb0000000
[4294675.648000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294675.648000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.648000] hub 5-0:1.0: USB hub found
[4294675.648000] hub 5-0:1.0: 8 ports detected
[4294675.701000] b44.c:v0.95 (Aug 3, 2004)
[4294675.701000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294675.704000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:14:22:8e:b7:91
[4294676.063000] usb 1-1: device not accepting address 2, error -71
[4294676.583000] usb 1-1: new full speed USB device using uhci_hcd and address 4[4294677.731000] SCSI subsystem initialized
[4294677.733000] Initializing USB Mass Storage driver...
[4294677.734000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294677.734000] usb-storage: device found at 4
[4294677.734000] usb-storage: waiting for device to settle before scanning
[4294677.734000] usbcore: registered new driver usb-storage
[4294677.734000] USB Mass Storage support registered.
[4294678.081000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294678.081000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294678.087000] ACPI: Thermal Zone [THM] (52 C)
[4294678.304000] Attempting manual resume
[4294678.304000] swsusp: Suspend partition has wrong signature?
[4294678.316000] kjournald starting.  Commit interval 5 seconds
[4294678.316000] EXT3-fs: mounted filesystem with ordered data mode.
[4294679.683000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294682.673000] Adding 8024k swap on /dev/hda3.  Priority:-1 extents:1
[4294682.745000]   Vendor:           Model:                   Rev:
[4294682.745000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294682.750000] usb-storage: device scan complete
[4294682.970000] EXT3 FS on hda4, internal journal
[4294689.367000] SCSI device sda: 1019617 512-byte hdwr sectors (522 MB)
[4294689.370000] sda: Write Protect is off
[4294689.370000] sda: Mode Sense: 00 c0 00 00
[4294689.370000] sda: assuming drive cache: write through
[4294689.380000] SCSI device sda: 1019617 512-byte hdwr sectors (522 MB)
[4294689.383000] sda: Write Protect is off
[4294689.383000] sda: Mode Sense: 00 c0 00 00
[4294689.383000] sda: assuming drive cache: write through
[4294689.383000]  /dev/scsi/host0/bus0/target0/lun0: unknown partition table
[4294689.409000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4294690.290000] lp: driver loaded but no devices found
[4294690.325000] mice: PS/2 mouse device common for all mice
[4294690.590000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294690.957000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[4294690.960000] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[4294691.110000] ts: Compaq touchscreen protocol output
[4294691.607000] cdrom: open failed.
[4294692.285000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294692.378000] NTFS volume version 3.1.
[4294693.850000] Linux agpgart interface v0.101 (c) Dave Jones
[4294693.858000] agpgart: Detected an Intel 915GM Chipset.
[4294693.859000] agpgart: Detected 7932K stolen memory.
[4294693.891000] agpgart: AGP aperture is 256M @ 0xc0000000
[4294694.082000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294694.083000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[4294694.845000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294694.850000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294694.850000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294694.939000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294694.939000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294695.840000] hw_random: RNG not detected
[4294697.740000] Real Time Clock Driver v1.12
[4294697.828000] input: PC Speaker
[4294698.826000] NET: Registered protocol family 17
[4294699.855000] b44: eth0: Link is down.
[4294762.804000] ACPI: AC Adapter [AC] (on-line)
[4294763.121000] ACPI: Battery Slot [BAT0] (battery present)
[4294763.141000] ACPI: Lid Switch [LID]
[4294763.141000] ACPI: Power Button (CM) [PBTN]
[4294763.141000] ACPI: Sleep Button (CM) [SBTN]
[4294763.252000] ibm_acpi: ec object not found
[4294763.373000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294763.373000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[4294770.883000] [drm] Initialized drm 1.0.0 20040925
[4294770.892000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294770.896000] [drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
[4294770.897000] mtrr: base(0xc0020000) is not aligned on a size(0x300000) boundary
[4294774.383000] apm: BIOS not found.
[4294774.698000] Linux Kernel Card Services
[4294774.698000]   options:  [pci] [cardbus] [pm]
[4294774.730000] Intel ISA PCIC probe: not found.
[4294774.731000] Unable to handle kernel NULL pointer dereference at virtual address 00000000
[4294774.731000]  printing eip:
[4294774.731000] c0112cac
[4294774.731000] *pde = 00000000
[4294774.731000] Oops: 0000 [#1]
[4294774.731000] Modules linked in: i82365 rsrc_nonstatic pcmcia_core i915 drm video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi i2c_acpi_ec i2c_core button battery container ac af_packet pcspkr rtc tpm_nsc tpm pci_hotplug snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc intel_agp agpgart nls_iso8859_1 vfat fat nls_cp437 ntfs joydev tsdev dm_mod evdev psmouse mousedev parport_pc lp parport sd_mod md ext3 jbd thermal processor fan usb_storage scsi_mod b44 mii ehci_hcd uhci_hcd usbcore ide_cd cdrom ide_disk ide_generic piix ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
[4294774.731000] CPU:    0
[4294774.731000] EIP:    0060:[<c0112cac>]    Not tainted VLI
[4294774.731000] EFLAGS: 00010086   (2.6.12-9-386)
[4294774.731000] EIP is at __wake_up_common+0xf/0x47
[4294774.731000] eax: d03e7c48   ebx: 00000001   ecx: d03e3e30   edx: 00000000
[4294774.731000] esi: c02ea2c8   edi: d03e7c48   ebp: c7071f38   esp: c7071f28
[4294774.731000] ds: 007b   es: 007b   ss: 0068
[4294774.731000] Process modprobe (pid: 7322, threadinfo=c7070000 task=c769f5a0)[4294774.731000] Stack: c02ea2e0 00000286 c02ea2c8 c02ea2e0 c7071f58 c0112d5a d03e7c48 00000003
[4294774.731000]        00000001 00000000 00000000 d03e696c c02ea5c4 c019965b d03e6948 d03e6984
[4294774.731000]        c0199680 c0000000 c7070000 c0199d92 d03e696c 00000000 d03e68c0 c01996a0
[4294774.731000] Call Trace:
[4294774.731000]  [<c0112d5a>] complete+0x1a/0x24
[4294774.731000]  [<c019965b>] kobject_cleanup+0x40/0x65
[4294774.731000]  [<c0199680>] kobject_release+0x0/0xa
[4294774.731000]  [<c0199d92>] kref_put+0x46/0x54
[4294774.731000]  [<c01996a0>] kobject_put+0x16/0x19
[4294774.731000]  [<c0199680>] kobject_release+0x0/0xa
[4294774.731000]  [<d03f5da8>] init_i82365+0x70/0x165 [i82365]
[4294774.731000]  [<c0129682>] sys_init_module+0xb5/0x172
[4294774.731000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4294774.731000] Code: 08 03 8d 65 f4 5b 5e 5f 5d c3 55 89 e5 8b 45 08 8b 50 04 89 55 08 5d e9 07 f8 ff ff 55 89 e5 57 56 53 57 8b 7d 08 8b 5d 10 8b 17 <8b> 02 39 fa 89 45 f0 74 27 8b 72 f4 ff 75 18 8d 42 f4 ff 75 14
[4294774.731000]  <6>Bluetooth: Core ver 2.7
[4294775.634000] NET: Registered protocol family 31
[4294775.634000] Bluetooth: HCI device and connection manager initialized
[4294775.634000] Bluetooth: HCI socket layer initialized
[4294775.734000] Bluetooth: L2CAP ver 2.7
[4294775.734000] Bluetooth: L2CAP socket layer initialized
[4294775.758000] Bluetooth: RFCOMM ver 1.5
[4294775.758000] Bluetooth: RFCOMM socket layer initialized
[4294775.758000] Bluetooth: RFCOMM TTY layer initialized
[4294787.357000] NET: Registered protocol family 10
[4294787.357000] Disabled Privacy Extensions on device c02eb280(lo)
[4294787.359000] IPv6 over IPv4 tunneling driver
[4294797.451000] eth0: no IPv6 routers present
[4294798.555000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294851.451000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294851.586000] ndiswrapper (ndiswrapper_load_driver:92): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
martin@ubuntu:~$

confused why ndiswrapper failed

---

