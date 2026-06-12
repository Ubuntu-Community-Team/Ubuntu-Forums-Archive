---
title: "Ipod not detecting when connected"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by JarekErvin on 2006-12-17
Hey,
      I am a recent convert to Ubuntu 6.10 from Windows, and I've been getting around alright and solving problems fairly well, but I've run into a pitfall with my ipod.

The ipod doesn't autodetect when I plug it in.  I have a third generation 15Gig ipod, and it is fairly shoddy, but I can't justify buying a new one as I don't use it very often.  It is already formated with the FAT32 file system and has a decent chunk of the hard drive used as I was syncing my pod in XP prior to using Ubuntu.

When i plug in external hard drives and anything else I can think of sticking into my USB port, it loads, so I know my USB is at least functional.

I have looked at a number of guides to using an Ipod in Linux as well as nearly all the threads about Ipods here, but all those guides work on the assumption that the ipod will simply detect when plugged in.  Because of this as well as the fact that my computer detects other types of hard drives, I'm guessing something is a problem.

Am I missing drivers or something of that sort that I need to get the darn thing to detect?

Thanks in advance for the assistance.

Also, I've ran into a lot of new areas and issues that I wouldn't know what to do about if not for the awesome community here.  Thanks a lot for the great work!

Jarek

---

### Post by xyz on 2006-12-18
Hi 
Please post the outputs of:
```
sudo fdisk -l
and
cat /etc/fstab
```
with it plugged in.

---

### Post by JarekErvin on 2006-12-18
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11973    96173091   83  Linux
/dev/hda2           11974       12161     1510110    5  Extended
/dev/hda5           11974       12161     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24792   199141708+  83  Linux

 
and



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=aeb644d3-e1d9-49a2-9d3f-aba63e9045d9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=26e3527b-2939-4223-873c-c9cc22b524cc none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1 /media/storage ext3 defaults 0 0


Jarek

---

### Post by xyz on 2006-12-19
Please post the output of:
```
dmesg
```
If somewhere in there it says something like:
> USB device using ehci_hcd 
then run in a terminal:
```
sudo modprobe -r ehci_hcd 
```
See if it works. Plug it in when already in Gnome.

---

### Post by JarekErvin on 2006-12-19
Heres the section I found pertinent:

[17179577.464000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[17179577.656000] usb 1-1: configuration #1 chosen from 1 choice
[17179577.900000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[17179578.024000] usb 2-2: device descriptor read/64, error -71
[17179578.252000] usb 2-2: device descriptor read/64, error -71
[17179578.468000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[17179578.592000] usb 2-2: device descriptor read/64, error -71
[17179578.820000] usb 2-2: device descriptor read/64, error -71
[17179579.036000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[17179579.452000] usb 2-2: device not accepting address 4, error -71
[17179579.564000] usb 2-2: new full speed USB device using uhci_hcd and address 5
[17179579.980000] usb 2-2: device not accepting address 5, error -71
[17179585.452000] 8139too Fast Ethernet driver 0.9.27
[17179585.452000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 185
[17179585.452000] eth0: RealTek RTL8139 at 0xf885a000, 00:40:05:88:1f:26, IRQ 185
[17179585.452000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179585.460000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179585.464000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[17179585.464000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[17179585.464000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 193
[17179585.464000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 1
[17179585.468000] eth1: VIA Rhine II at 0x1cc00, 00:50:2c:07:88:1c, IRQ 193.
[17179585.468000] eth1: MII PHY found at address 1, status 0x7809 advertising 01e1 Link 0000.
[17179585.632000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179585.636000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179585.952000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 201
[17179585.952000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 185
[17179586.044000] Floppy drive(s): fd0 is 1.44M
[17179586.064000] FDC 0 is a post-1991 82077
[17179586.084000] input: PC Speaker as /class/input/input1
[17179586.244000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.248000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[17179586.252000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179586.280000] usbcore: registered new driver hiddev
[17179586.328000] irda_init()
[17179586.328000] NET: Registered protocol family 23
[17179586.336000] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input2
[17179586.336000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.0-1
[17179586.336000] usbcore: registered new driver usbhid
[17179586.336000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179586.712000] eth1: link down
[17179586.796000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179586.944000] parport: PnPBIOS parport detected.
[17179586.944000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179586.988000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179587.128000] ts: Compaq touchscreen protocol output
[17179587.528000] lp0: using parport0 (interrupt-driven).
[17179587.572000] Adding 1510068k swap on /dev/disk/by-uuid/26e3527b-2939-4223-873c-c9cc22b524cc.  Priority:-1 extents:1 across:1510068k
[17179587.628000] EXT3 FS on hda1, internal journal
[17179587.764000] NET: Registered protocol family 17
[17179587.852000] kjournald starting.  Commit interval 5 seconds
[17179587.864000] EXT3 FS on hdb1, internal journal
[17179587.864000] EXT3-fs: mounted filesystem with ordered data mode.
[17179590.416000] NET: Registered protocol family 10
[17179590.416000] lo: Disabled Privacy Extensions
[17179590.416000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179590.416000] IPv6 over IPv4 tunneling driver
[17179592.636000] ACPI: Power Button (FF) [PWRF]
[17179592.636000] ACPI: Power Button (CM) [PWRB]
[17179592.636000] ACPI: Sleep Button (CM) [SLPB]
[17179592.804000] ibm_acpi: ec object not found
[17179592.836000] pcc_acpi: loading...
[17179595.016000] [drm] Initialized drm 1.0.1 20051102
[17179595.024000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 217
[17179595.028000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179595.752000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179595.752000] apm: overridden by ACPI.
[17179596.308000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179596.308000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179596.308000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17179596.604000] [drm] Setting GART location based on new memory map
[17179596.604000] [drm] Loading R200 Microcode
[17179596.604000] [drm] writeback test succeeded in 1 usecs
[17179600.412000] Bluetooth: Core ver 2.8
[17179600.412000] NET: Registered protocol family 31
[17179600.412000] Bluetooth: HCI device and connection manager initialized
[17179600.412000] Bluetooth: HCI socket layer initialized
[17179600.452000] Bluetooth: L2CAP ver 2.8
[17179600.452000] Bluetooth: L2CAP socket layer initialized
[17179600.504000] Bluetooth: RFCOMM socket layer initialized
[17179600.504000] Bluetooth: RFCOMM TTY layer initialized
[17179600.504000] Bluetooth: RFCOMM ver 1.7
[17179600.740000] eth0: no IPv6 routers present
[17179602.436000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179602.436000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179602.436000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17179602.720000] [drm] Setting GART location based on new memory map
[17179602.720000] [drm] Loading R200 Microcode
[17179602.720000] [drm] writeback test succeeded in 1 usecs
[17179899.224000] usb 2-2: new full speed USB device using uhci_hcd and address 6
[17179899.344000] usb 2-2: device descriptor read/64, error -71
[17179899.568000] usb 2-2: device descriptor read/64, error -71
[17179899.784000] usb 2-2: new full speed USB device using uhci_hcd and address 7
[17179899.904000] usb 2-2: device descriptor read/64, error -71
[17179900.128000] usb 2-2: device descriptor read/64, error -71
[17179900.344000] usb 2-2: new full speed USB device using uhci_hcd and address 8
[17179900.760000] usb 2-2: device not accepting address 8, error -71
[17179900.872000] usb 2-2: new full speed USB device using uhci_hcd and address 9
[17179901.284000] usb 2-2: device not accepting address 9, error -71
[17179903.256000] usb 2-2: new full speed USB device using uhci_hcd and address 10
[17179903.376000] usb 2-2: device descriptor read/64, error -71
[17179903.600000] usb 2-2: device descriptor read/64, error -71
[17179903.816000] usb 2-2: new full speed USB device using uhci_hcd and address 11
[17179903.940000] usb 2-2: device descriptor read/64, error -71
[17179904.168000] usb 2-2: device descriptor read/64, error -71
[17179904.384000] usb 2-2: new full speed USB device using uhci_hcd and address 12
[17179904.796000] usb 2-2: device not accepting address 12, error -71
[17179904.908000] usb 2-2: new full speed USB device using uhci_hcd and address 13
[17179905.316000] usb 2-2: device not accepting address 13, error -71


There was no ehci_hcd, but there was a uhci_hcd error...  I don't know if that helps.

Thanks,
Jarek

---

