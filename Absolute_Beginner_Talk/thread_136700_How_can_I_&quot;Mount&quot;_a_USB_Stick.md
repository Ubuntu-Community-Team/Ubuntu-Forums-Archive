---
title: "How can I &quot;Mount&quot; a USB Stick?"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-26
Hello ALL !!!

I would like to know how can I "mount" a USB Stick.

I have never read any tutorial about that...


I wonder whether I need to format this...

OR:

Are  USB sticks always FAT32?


What do I type, to mount it?

mount    -t    vfat      /media/usb_stick_drive   iocharset=utf8,umask=000  0  0 ?

OR: is it "automounted",  & where would I look (in which folder) to access it?

Thanks.

---

### Post by curtis on 2006-02-26
If you are using GNOME, most likely it would of been auto-mounted.
So look in /media

If your using KDE, I'm not sure if it gets auto-mounted but manually mounting it should be fine.
And about the file system of usb sticks, most manufacturs format them as VFAT by default.
But you can easily re-format them to the file system of your choice.
I hope that helps answer your questions.

---

### Post by patrick295767 on 2006-02-26
```
dmesg
#place ur usb stick
dmesg 
look where is ur usb stick (normally /dev/sda1)
sudo mkdir /mnt/myusbstick
sudo mount -t vfat /dev/sda1 /mnt/myusbstick

rox /mnt/         #to look at it ... 
``` 
  
Or you can add it in ur /etc/fstab

Greetz

---

### Post by manicka on 2006-02-26
In gnome it should automount and an icon should appear on your desktop

---

### Post by dvarsam on 2006-02-26
[QUOTE=manicka]In gnome it should automount and an icon should appear on your desktop[/QUOTE]
Ok guys, just to make things clear:

I am using Ubuntu 5.10 - so that should be Gnome.

it is not in media (there i see other stuff):

root@house:/# cd media
root@house:/media# ls
cdrom  cdrom0  floppy  floppy0  sda2  sda5
root@house:/media#

Sda2 & Sda5 are two partitions where I want to test other Linux OS's

Then I thought doing what "Patrick" suggested:

root@house:/# cd mnt
root@house:/mnt# ls
myusbstick
root@house:/mnt#

But then again it is NOT "sda1" either (that is reserved for other Hard Drive)!.

Then I thought abou "manicka's" view & it is NOT on my Desktop either!

However, when I plug it in, it flashes (only once & that is it!).

Then I thought to type "fdisk -l":

root@house:/# fdisk -l

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433        6079    29294527+  83  Linux
/dev/sda3            6080       10011    31583790    f  W95 Ext'd (LBA)
/dev/sda5            6080       10011    31583758+   b  W95 FAT32

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10416    83666488+   7  HPFS/NTFS
/dev/sdb2           10417       14593    33551752+   f  W95 Ext'd (LBA)
/dev/sdb5           10417       14593    33551721    b  W95 FAT32
root@house:/#
root@house:/#

I do NOT see it there either...

Where is it?

Thanks.

---

### Post by patrick295767 on 2006-02-26
[QUOTE=dvarsam]Ok guys, just to make things clear:

I am using Ubuntu 5.10 - so that should be Gnome.

it is not in media (there i see other stuff):

root@house:/# cd media
root@house:/media# ls
cdrom  cdrom0  floppy  floppy0  sda2  sda5
root@house:/media#

Sda2 & Sda5 are two partitions where I want to test other Linux OS's

Then I thought doing what "Patrick" suggested:

root@house:/# cd mnt
root@house:/mnt# ls
myusbstick
root@house:/mnt#

But then again it is NOT "sda1" either (that is reserved for other Hard Drive)!.

Then I thought abou "manicka's" view & it is NOT on my Desktop either!

However, when I plug it in, it flashes (only once & that is it!).

Then I thought to type "fdisk -l":

root@house:/# fdisk -l

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433        6079    29294527+  83  Linux
/dev/sda3            6080       10011    31583790    f  W95 Ext'd (LBA)
/dev/sda5            6080       10011    31583758+   b  W95 FAT32

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10416    83666488+   7  HPFS/NTFS
/dev/sdb2           10417       14593    33551752+   f  W95 Ext'd (LBA)
/dev/sdb5           10417       14593    33551721    b  W95 FAT32
root@house:/#
root@house:/#

I do NOT see it there either...

Where is it?

Thanks.[/QUOTE]
  
Please, Unplug your usbstick
Now, Replug ur usbstick
in ur konsole, plz type : dmesg 
and post it ... 
  
Then, we will konw what you need to enter instead of /dev/sdaxxx in this line: 
```
sudo mount -t vfat /dev/sdaxxx /mnt/myusbstick
```
 
Greetings, 

Patrick

---

### Post by steve.horsley on 2006-02-26
Since sda and sdb are already used, maybe it's coming as sdc. 

Try the command:
sudo tail -f /var/log/messages
and watch what gets logged as you plug the stick in. Those messages may well help in debugging.

---

### Post by dvarsam on 2006-02-26
Ok, here is what I get after typing:

"sudo tail -f /var/log/messages"

Feb 27 00:00:13 localhost kernel: [4313892.218000] usb 2-2: new full speed USB device using uhci_hcd and address 8
Feb 27 00:00:13 localhost kernel: [4313892.370000] scsi8 : SCSI emulation for USB Mass Storage devices
Feb 27 00:00:18 localhost kernel: [4313897.374000]   Vendor: 3SYSTEM   Model: USB FLASH DISK    Rev: 1.00
Feb 27 00:00:18 localhost kernel: [4313897.374000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Feb 27 00:00:18 localhost kernel: [4313897.389000] SCSI device sdg: 64000 512-byte hdwr sectors (33 MB)
Feb 27 00:00:18 localhost kernel: [4313897.399000] sdg: Write Protect is off
Feb 27 00:00:18 localhost kernel: [4313897.416000] SCSI device sdg: 64000 512-byte hdwr sectors (33 MB)
Feb 27 00:00:18 localhost kernel: [4313897.426000] sdg: Write Protect is off
Feb 27 00:00:18 localhost kernel: [4313897.426000]  /dev/scsi/host8/bus0/target0/lun0: p1
Feb 27 00:00:18 localhost kernel: [4313897.505000] Attached scsi removable disk sdg at scsi8, channel 0, id 0, lun 0

Sorry, but I can NOT get a clue from the above...

It does NOT specifically state "sda1" or "hda4" or "whatever"...

Can you make something out of it?

Thanks.

---

### Post by cwaldbieser on 2006-02-26
[QUOTE=dvarsam]Ok, here is what I get after typing:

"sudo tail -f /var/log/messages"

Feb 27 00:00:13 localhost kernel: [4313892.218000] usb 2-2: new full speed USB device using uhci_hcd and address 8
Feb 27 00:00:13 localhost kernel: [4313892.370000] scsi8 : SCSI emulation for USB Mass Storage devices
Feb 27 00:00:18 localhost kernel: [4313897.374000]   Vendor: 3SYSTEM   Model: USB FLASH DISK    Rev: 1.00
Feb 27 00:00:18 localhost kernel: [4313897.374000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Feb 27 00:00:18 localhost kernel: [4313897.389000] SCSI device sdg: 64000 512-byte hdwr sectors (33 MB)
Feb 27 00:00:18 localhost kernel: [4313897.399000] sdg: Write Protect is off
Feb 27 00:00:18 localhost kernel: [4313897.416000] SCSI device sdg: 64000 512-byte hdwr sectors (33 MB)
Feb 27 00:00:18 localhost kernel: [4313897.426000] sdg: Write Protect is off
Feb 27 00:00:18 localhost kernel: [4313897.426000]  /dev/scsi/host8/bus0/target0/lun0: p1
Feb 27 00:00:18 localhost kernel: [4313897.505000] Attached scsi removable disk sdg at scsi8, channel 0, id 0, lun 0

Sorry, but I can NOT get a clue from the above...

It does NOT specifically state "sda1" or "hda4" or "whatever"...

Can you make something out of it?

Thanks.[/QUOTE]

Looks like it is /dev/sdg.

---

### Post by lukem on 2006-02-26
Try mounting it the way Patrick295767 suggested as /dev/sdg
You may also want to look under
System
Preferences
Removable Drives and Media
and check to see that the options are checked to mount removable drives and media when they are plugged in.
Good Luck

---

### Post by dvarsam on 2006-02-26
So, if it is indeed "/dev/sdg",  I then try to "mount" like this:

root@house:/#
root@house:/# mount -t vfat /dev/sdg /mnt/myusbstick
mount: special device /dev/sdg does not exist
root@house:/#

What does it mean "it does Not exist"?


Are USB Sticks usually vfat or could it be NTFS?

I do not know what to do....

---

### Post by lukem on 2006-02-26
Have you looked under "System" "Preferences" "Removable Drives and Media" yet?  I'm not sure they are checked by default or not.  In Gnome it should put an icon on your desktop when the stick is plugged in.

---

### Post by dvarsam on 2006-02-26
Yes, under "System\Preferences\Removable Drives & Media", these are checked:

1. Mount removable drives when hot-plugged    ---> checked
2. Mount removable media when inserted          ---> checked
3. Browse removable media when inserted        ---> checked
4. Auto-run programs on new drives & media     ---> not checked

Any other suggestions?

---

### Post by cwaldbieser on 2006-02-27
[QUOTE=dvarsam]So, if it is indeed "/dev/sdg",  I then try to "mount" like this:

root@house:/#
root@house:/# mount -t vfat /dev/sdg /mnt/myusbstick
mount: special device /dev/sdg does not exist
root@house:/#

What does it mean "it does Not exist"?


Are USB Sticks usually vfat or could it be NTFS?

I do not know what to do....[/QUOTE]

Well, I guess the easiest thing would be to see if the device file is actually there after you check dmesg.
```

$ ls /dev/sdg*

```
If it's not there, then I am not sure what's going on.

---

### Post by patrick295767 on 2006-02-27
[QUOTE=patrick295767]Please, Unplug your usbstick
Now, Replug ur usbstick
in ur konsole, plz type : dmesg 
and post it ... 
  
Then, we will konw what you need to enter instead of /dev/sdaxxx in this line: 
```
sudo mount -t vfat /dev/sdaxxx /mnt/myusbstick
```
 
Greetings, 

Patrick[/QUOTE]
  
Plz coudl you post the result of dmesg to have a quick look ... 
via:
```
Now, Replug ur usbstick
in ur konsole, plz type : dmesg 
and post it ... 
```
  
Thank you,

Patrick

---

### Post by dvarsam on 2006-02-27
I finally got it to work !!!

But the only way to make it work, is to plug it in, then Stutdown & Restart Ubuntu.

If I boot while it is plugged, I can then see it.
If I do it after I have Booted, then Nothing...

Aren't USB sticks supposed to be Hot-pluggable?

Or is it Ubuntu that does NOT support it...

By the way, the output you asked:

root@house:~# dmesg
.481000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4294676.507000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus num ber 4
[4294676.507000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[4294676.507000] hub 4-0:1.0: USB hub found
[4294676.507000] hub 4-0:1.0: 2 ports detected
[4294676.540000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> I RQ 23
[4294676.540000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294676.540000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801EB/ER (ICH5/ICH5R ) USB2 EHCI Controller
[4294676.540000] ehci_hcd 0000:00:1d.7: debug port 1
[4294676.540000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus num ber 5
[4294676.540000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe200000
[4294676.544000] PCI: cache line size of 128 is not supported by device 0000:00: 1d.7
[4294676.544000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 1 0 Dec 2004
[4294676.544000] hub 5-0:1.0: USB hub found
[4294676.544000] hub 5-0:1.0: 8 ports detected
[4294676.623000] Intel(R) PRO/1000 Network Driver - version 6.0.54-k2
[4294676.624000] Copyright (c) 1999-2004 Intel Corporation.
[4294676.624000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> I RQ 18
[4294676.624000] PCI: Setting latency timer of device 0000:02:01.0 to 64
[4294676.944000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[4294676.955000] usb 1-1: device not accepting address 2, error -71
[4294678.208000] usb 5-6: new high speed USB device using ehci_hcd and address 6
[4294678.464000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[4294678.713000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[4294678.984000] Initializing USB Mass Storage driver...
[4294679.028000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[4294679.284000] usb 1-2: new low speed USB device using uhci_hcd and address 5
[4294679.581000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294679.581000] usb-storage: device found at 6
[4294679.581000] usb-storage: waiting for device to settle before scanning
[4294679.583000] scsi3 : SCSI emulation for USB Mass Storage devices
[4294679.583000] usb-storage: device found at 3
[4294679.583000] usb-storage: waiting for device to settle before scanning
[4294679.583000] usbcore: registered new driver usb-storage
[4294679.583000] USB Mass Storage support registered.
[4294680.328000] ACPI: CPU0 (power states: C1[C1])
[4294680.328000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294680.572000] kjournald starting.  Commit interval 5 seconds
[4294680.572000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.353000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294684.582000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 0125
[4294684.582000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294684.586000]   Vendor: 3SYSTEM   Model: USB FLASH DISK    Rev: 1.00
[4294684.586000]   Type:   Direct-Access                      ANSI SCSI revision : 02
[4294684.630000] Attached scsi removable disk sdc at scsi2, channel 0, id 0, lun  0
[4294684.632000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 0125
[4294684.632000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294684.640000] SCSI device sdd: 64000 512-byte hdwr sectors (33 MB)
[4294684.651000] sdd: Write Protect is off
[4294684.651000] sdd: Mode Sense: 0b 00 00 08
[4294684.651000] sdd: assuming drive cache: write through
[4294684.667000] SCSI device sdd: 64000 512-byte hdwr sectors (33 MB)
[4294684.677000] sdd: Write Protect is off
[4294684.677000] sdd: Mode Sense: 0b 00 00 08
[4294684.677000] sdd: assuming drive cache: write through
[4294684.677000]  /dev/scsi/host3/bus0/target0/lun0: p1
[4294684.686000] Attached scsi removable disk sdd at scsi3, channel 0, id 0, lun  0
[4294684.687000] usb-storage: device scan complete
[4294684.692000] Attached scsi removable disk sde at scsi2, channel 0, id 0, lun  1
[4294684.694000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 0125
[4294684.694000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294684.702000] Attached scsi removable disk sdf at scsi2, channel 0, id 0, lun  2
[4294684.704000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 0125
[4294684.704000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294684.709000] Attached scsi removable disk sdg at scsi2, channel 0, id 0, lun  3
[4294684.711000] usb-storage: device scan complete
[4294685.152000] EXT3 FS on sda1, internal journal
[4294689.626000] parport: PnPBIOS parport detected.
[4294689.626000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294689.713000] lp0: using parport0 (interrupt-driven).
[4294689.756000] mice: PS/2 mouse device common for all mice
[4294689.793000] ieee1394: Initialized config rom entry `ip1394'
[4294689.798000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294690.091000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294690.180000] ts: Compaq touchscreen protocol output
[4294692.352000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294693.048000] cdrom: open failed.
[4294694.066000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294694.118000] NTFS volume version 3.1.
[4294694.133000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294694.190000] NTFS volume version 3.1.
[4294695.313000] Linux agpgart interface v0.101 (c) Dave Jones
[4294695.321000] agpgart: Detected an Intel 865 Chipset.
[4294695.342000] agpgart: AGP aperture is 128M @ 0xf0000000
[4294695.424000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294695.435000] shpchp: shpc_init : shpc_cap_offset == 0
[4294695.435000] shpchp: shpc_init : shpc_cap_offset == 0
[4294695.435000] shpchp: shpc_init : shpc_cap_offset == 0
[4294695.435000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294695.846000] hw_random hardware driver 1.0.0 loaded
[4294696.340000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> I RQ 17
[4294696.340000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294696.652000] intel8x0_measure_ac97_clock: measured 49379 usecs
[4294696.652000] intel8x0: clocking to 48000
[4294697.378000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294697.378000] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 17 (level, low) -> I RQ 17
[4294697.383000] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[4294697.435000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fe1000 00-fe1007ff]  Max Packet=[2048]
[4294698.708000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0007e90000649773]
[4294699.059000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer de v 4 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1073
[4294699.065000] usbcore: registered new driver usblp
[4294699.065000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driv er
[4294699.193000] usbcore: registered new driver hiddev
[4294700.026000] hiddev96: USB HID v1.10 Device [American Power Conversion Back- UPS RS 500 FW:30.j5.I USB FW:j5] on usb-0000:00:1d.0-2
[4294700.026000] usbcore: registered new driver usbhid
[4294700.026000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294700.159000] usbcore: registered new driver usbserial
[4294700.163000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
[4294700.167000] usbcore: registered new driver usbserial_generic
[4294700.167000] drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
[4294700.175000] drivers/usb/serial/usb-serial.c: USB Serial support registered for PL-2303
[4294700.179000] pl2303 2-1:1.0: PL-2303 converter detected
[4294700.184000] usb 2-1: PL-2303 converter now attached to ttyUSB0
[4294700.184000] usbcore: registered new driver pl2303
[4294700.184000] drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adap tor driver v0.12
[4294700.470000] Real Time Clock Driver v1.12
[4294700.669000] input: PC Speaker
[4294700.729000] Floppy drive(s): fd0 is 1.44M
[4294700.756000] FDC 0 is a National Semiconductor PC87306
[4294701.023000] ide-floppy driver 0.99.newide
[4294701.029000] hda: No disk in drive
[4294701.036000] hda: 735232kB, 718/64/32 CHS, 4096 kBps, 512 sector size, 3676 rpm
[4294702.607000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[4294702.618000] NET: Registered protocol family 17
[4294703.572000] NET: Registered protocol family 10
[4294703.572000] Disabled Privacy Extensions on device c02eb280(lo)
[4294703.572000] IPv6 over IPv4 tunneling driver
[4294704.930000] ACPI: Power Button (FF) [PWRF]
[4294704.930000] ACPI: Sleep Button (CM) [SLPB]
[4294705.042000] ibm_acpi: ec object not found
[4294711.637000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294711.637000] apm: overridden by ACPI.
[4294713.415000] Bluetooth: Core ver 2.7
[4294713.415000] NET: Registered protocol family 31
[4294713.415000] Bluetooth: HCI device and connection manager initialized
[4294713.415000] Bluetooth: HCI socket layer initialized
[4294713.433000] Bluetooth: L2CAP ver 2.7
[4294713.433000] Bluetooth: L2CAP socket layer initialized
[4294713.447000] Bluetooth: RFCOMM ver 1.5
[4294713.447000] Bluetooth: RFCOMM socket layer initialized
[4294713.447000] Bluetooth: RFCOMM TTY layer initialized
[4294714.369000] eth0: no IPv6 routers present
[4294728.116000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4296556.433000] NTFS volume version 3.1.
[4296556.453000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4296556.512000] NTFS volume version 3.1.
[4299361.111000] NTFS volume version 3.1.
[4299361.133000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4299361.189000] NTFS volume version 3.1.
[4300781.390000] NTFS volume version 3.1.
[4300781.391000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4300781.479000] NTFS volume version 3.1.
[4313708.887000] e1000: eth0: e1000_watchdog_task: NIC Link is Down
[4313712.487000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[4316144.127000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4316144.127000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4316144.199000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4316144.199000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4316936.777000] e1000: eth0: e1000_watchdog_task: NIC Link is Down
[4316939.475000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[4321393.171000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4321393.171000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4321393.240000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4321393.240000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4330852.386000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4330852.386000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4330852.462000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4330852.462000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4330890.828000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4330890.828000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4330890.903000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4330890.903000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4330993.418000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4330993.418000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4330993.479000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4330993.479000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4331541.717000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4331541.717000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4331541.804000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4331541.804000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.132000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4333406.132000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.199000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4333406.199000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.265000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4333406.265000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.326000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4333406.326000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.378000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4333406.378000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.433000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4333406.433000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.479000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4333406.479000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.549000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4333406.549000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.609000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4333406.609000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.650000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4333406.650000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.824000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4333406.824000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333406.887000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4333406.887000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4334428.919000] usb 2-2: USB disconnect, address 3
[4334431.796000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[4334431.948000] scsi4 : SCSI emulation for USB Mass Storage devices
[4334431.949000] usb-storage: device found at 4
[4334431.949000] usb-storage: waiting for device to settle before scanning
[4334436.952000]   Vendor: 3SYSTEM   Model: USB FLASH DISK    Rev: 1.00
[4334436.952000]   Type:   Direct-Access                      ANSI SCSI revision : 02
[4334436.967000] SCSI device sdh: 64000 512-byte hdwr sectors (33 MB)
[4334436.981000] sdh: Write Protect is off
[4334436.981000] sdh: Mode Sense: 0b 00 00 08
[4334436.981000] sdh: assuming drive cache: write through
[4334437.006000] SCSI device sdh: 64000 512-byte hdwr sectors (33 MB)
[4334437.017000] sdh: Write Protect is off
[4334437.017000] sdh: Mode Sense: 0b 00 00 08
[4334437.017000] sdh: assuming drive cache: write through
[4334437.017000]  /dev/scsi/host4/bus0/target0/lun0: p1
[4334437.101000] Attached scsi removable disk sdh at scsi4, channel 0, id 0, lun  0
[4334437.109000] usb-storage: device scan complete
root@house:~#

Is there a way to make it work without having to Shutdown & Reboot?

---

### Post by patrick295767 on 2006-02-28
In your dmesg result, 
I can read : > sdh: assuming drive cache: write through
which implies /dev/sdh
  
Ahh, there is also thsi possibility to check which /dev/sdxxx to use ... 
```
sudo apt-get -f -y qtparted
sudo qtparted
```
This can work (not always) to get  /dev/sdxxx informations.
  
Are you more user friendly now with Usbkeys mounting ?

Greetings, 

Pat'

---

### Post by ::DoGG:: on 2006-02-28
hELLO!
I know it`s more like AFTER post, but whatever...

The main thintg that guy was doing wrong was that he was using mount to mount /dev/dsg ( or wahetver hes device was) while mount command mounts PARTITIONS, NOT DISKS, if he would issue "mount /dev/sdg1" or  "/dev/sdh1" or 2 or 3 it would mount no problem - rebooting linux to mount usb stick is just.... well.. you know ...
The mount command returned that there is no such device, cause he was trying to mount the physical disks intead of the logical partitions.
Hope that helps anyone.

---

### Post by patrick295767 on 2006-03-02
[QUOTE=::DoGG::]hELLO!
I know it`s more like AFTER post, but whatever...

The main thintg that guy was doing wrong was that he was using mount to mount /dev/dsg ( or wahetver hes device was) while mount command mounts PARTITIONS, NOT DISKS, if he would issue "mount /dev/sdg1" or  "/dev/sdh1" or 2 or 3 it would mount no problem - rebooting linux to mount usb stick is just.... well.. you know ...
The mount command returned that there is no such device, cause he was trying to mount the physical disks intead of the logical partitions.
Hope that helps anyone.[/QUOTE]
  
Greeting DoGG ...
  
I hope he finally made it, and didnt give up ...   Linux is nice ! 
We'll hear about his progress  guess ... 

Pat'

---

### Post by dvarsam on 2006-03-03
Hello guys !

Thank you for your posts.

Dear Patrick:
Qtparted is awesome man !!!

Thank you !!!

With "QTParted", I can hot-plug my USB & see it quickly!

However, there is one thing that is missing:

From the Menu "File", under its options, there should be a "Refresh" option.

_Example_:
I launch QTParted (from the Ubuntu Menu, I select "Applications\System Tools\QTParted").
Then I can see ALL my Hard Drives...
Lets say I unplug my USB Stick...
& then I re-plug it back in...
... QTParted, unfortunately, can not see it...
If I want to see it again, I have to quit/close the program & re-load it/open it again (from the Ubuntu Menu, I have to re-select "Applications\System Tools\QTParted")

...if there were a button (e.g. from the Menu, select "File\Refresh"), which could re-check for any changes to my Hard Drives, it would be great !!!

Thank you again for all your help!

---

### Post by sYs^ on 2006-03-27
Hi, I'd like to mount my camera but when I plug it in nothing happens, no automount, nothing at /dev/sdxxx 

dmesg:

```
[4298006.273000] usb 2-2: new full speed USB device using ohci_hcd and address 4
[4298006.432000] usb 2-2: configuration #1 chosen from 1 choice
[4298006.435000] scsi1 : SCSI emulation for USB Mass Storage devices
[4298006.435000] usb-storage: device found at 4
[4298006.435000] usb-storage: waiting for device to settle before scanning
[4298011.443000]   Vendor: NIKON     Model: NIKON DSC E4800   Rev: 1.00
[4298011.443000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4298011.447000] usb-storage: device scan complete

```

How should I mount it? Thanks

---

### Post by The Running Board on 2006-03-30
Ok...Im relatively new to linux...but am lovin it so far. 

BUT...I am having the same problem as this guy was...and am in over my head.

My usb flash drives always would just pop right up like they should...then about an hour ago they just...didnt anymore...and Im a bit lost.

My dmesg looks like this:

>     
kyle@lappyUBUNTU64:~$ dmesg
0.000000] No AGP bridge found
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/hda2 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
[    0.000000] time.c: Using 3.579545 MHz PM timer.
[    0.000000] time.c: Detected 1790.855 MHz processor.
[   14.648441] time.c: Using PIT/TSC based timekeeping.
[   14.651892] Console: colour VGA+ 80x25
[   14.654366] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)[   14.657990] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.683912] Memory: 1020972k/1047808k available (1620k kernel code, 26124k reserved, 997k data, 136k init)
[   14.683959] Calibrating delay loop... 3522.56 BogoMIPS (lpj=1761280)
[   14.704465] Security Framework v1.0.0 initialized
[   14.704471] SELinux:  Disabled at boot.
[   14.704484] Mount-cache hash table entries: 256
[   14.704566] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)[   14.704569] CPU: L2 Cache: 512K (64 bytes/line)
[   14.704574] CPU: AMD Turion(tm) 64 Mobile Technology MT-32 stepping 02
[   14.704675] checking if image is initramfs... it is
[   15.108022] ACPI: Looking for DSDT in initrd... not found!
[   15.200640]  not found!
[   15.218842] Using local APIC timer interrupts.
[   15.274704] Detected 12.436 MHz APIC timer.
[   15.274718] testing NMI watchdog ... OK.
[   15.284770] NET: Registered protocol family 16
[   15.284792] ACPI: bus type pci registered
[   15.284799] PCI: Using configuration type 1
[   15.284802] mtrr: v2.0 (20020519)
[   15.285086] ACPI: Subsystem revision 20050729
[   15.288267] ACPI: Interpreter enabled
[   15.288270] ACPI: Using IOAPIC for interrupt routing
[   15.288519] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.288522] PCI: Probing PCI hardware (bus 00)
[   15.288553] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[   15.289650] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[   15.290004] Boot video device is 0000:01:00.0
[   15.290525] PCI: Transparent bridge - 0000:00:14.4
[   15.296564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.297303] burst-mode-ec-10-Aug
[   15.297305] ACPI: Embedded Controller [EC] (gpe 6)
[   15.302136] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP2._PRT]
[   15.303428] ACPI: PCI Interrupt Link [LNKA] (IRQs *5 6 7 10 11 12 14 15)
[   15.303633] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 6 7 10 11 12 14 15)
[   15.303825] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 7 *10 11 12 14 15)
[   15.304017] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 7 10 *11 12 14 15)
[   15.304209] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 6 *7 10 11 12 14 15)
[   15.304405] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[   15.304610] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[   15.304802] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[   15.304889] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.304901] pnp: PnP ACPI init
[   15.306209] pnp: PnP ACPI: found 10 devices
[   15.306293] usbcore: registered new driver usbfs
[   15.306311] usbcore: registered new driver hub
[   15.306343] PCI: Using ACPI for IRQ routing
[   15.306347] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.306461] PCI-DMA: Disabling IOMMU.
[   15.307220] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   15.307411] audit: initializing netlink socket (disabled)
[   15.307421] audit: initialized
[   15.307527] VFS: Disk quotas dquot_6.5.1
[   15.307560] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   15.307589] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   15.307594] devfs: boot_options: 0x0
[   15.307620] Initializing Cryptographic API
[   15.307721] PCI: 0000:00:02.0 has unsupported PM cap regs version (3)
[   15.307728] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   15.307731] pcie_portdrv_probe->Dev[5a34:1002] has invalid IRQ. Check vendor BIOS
[   15.307751] assign_interrupt_mode Found MSI capability
[   15.307754] Allocate Port Service[pcie00]
[   15.323029] Linux agpgart interface v0.101 (c) Dave Jones
[   15.323102] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   15.323278] i8042.c: Detected active multiplexing controller, rev 1.1.
[   15.323332] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   15.323349] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   15.323362] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   15.323374] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   15.323386] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.323390] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   15.325111] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   15.325122] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   15.325133] io scheduler noop registered
[   15.325149] io scheduler anticipatory registered
[   15.325155] io scheduler deadline registered
[   15.325163] io scheduler cfq registered
[   15.325460] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.325530] NET: Registered protocol family 2
[   15.334615] IP: routing cache hash table of 8192 buckets, 64Kbytes
[   15.334831] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[   15.337157] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.337757] TCP: Hash tables configured (established 262144 bind 65536)
[   15.337840] NET: Registered protocol family 8
[   15.337842] NET: Registered protocol family 20
[   15.337990] ACPI wakeup devices:
[   15.337992] POP2  RTL AC97 MC97
[   15.337996] ACPI: (supports S0 S1 S3 S4 S5)
[   15.338205] Freeing unused kernel memory: 136k freed
[   15.351957] vga16fb: initializing
[   15.351961] vga16fb: mapped to 0xffff8100000a0000
[   15.498661] Console: switching to colour frame buffer device 80x30
[   15.498666] fb0: VGA16 VGA frame buffer device
[   15.931766] input: AT Translated Set 2 keyboard on isa0060/serio0
[   16.663644] Capability LSM initialized
[   16.672828] NET: Registered protocol family 1
[   16.682515] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   16.682528] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   16.682532] ACPI: bus type ide registered
[   16.691204] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   16.691227] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   16.691238] ATIIXP: chipset revision 0
[   16.691241] ATIIXP: not 100% native mode: will probe irqs later
[   16.691252]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:pio
[   16.691267]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[   16.691276] Probing IDE interface ide0...
[   16.955310] hda: SAMSUNG MP0402H, ATA DISK drive
[   17.567115] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   17.567168] Probing IDE interface ide1...
[   18.239557] hdc: PHILIPS DVD+/-RW SDVD8441, ATAPI CD/DVD-ROM drive
[   18.851261] ide1 at 0x170-0x177,0x376 on irq 15
[   18.851351] Probing IDE interface ide2...
[   19.364333] Probing IDE interface ide3...
[   19.876431] Probing IDE interface ide4...
[   20.388532] Probing IDE interface ide5...
[   20.903939] hda: max request size: 1024KiB
[   21.336826] hda: 78242976 sectors (40060 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   21.337263] hda: cache flushes supported
[   21.337321]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 > p4
[   21.379388] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[   21.379395] Uniform CD-ROM driver Revision: 3.20
[   21.627555] Attempting manual resume
[   21.627793] swsusp: Suspend partition has wrong signature?
[   21.641553] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   21.641600] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   21.641620] ohci_hcd 0000:00:13.0: PCI device 1002:4374 (ATI Technologies Inc)
[   21.641816] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   21.641827] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfbdfd000
[   21.696839] hub 1-0:1.0: USB hub found
[   21.696851] hub 1-0:1.0: 4 ports detected
[   21.701804] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   21.701815] ohci_hcd 0000:00:13.1: PCI device 1002:4375 (ATI Technologies Inc)
[   21.701865] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   21.701871] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfbdfe000
[   21.756826] hub 2-0:1.0: USB hub found
[   21.756838] hub 2-0:1.0: 4 ports detected
[   21.771663] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   21.771683] ehci_hcd 0000:00:13.2: PCI device 1002:4373 (ATI Technologies Inc)
[   21.771740] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   21.771749] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbdff000
[   21.771806] ehci_hcd 0000:00:13.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[   21.771886] hub 3-0:1.0: USB hub found
[   21.771894] hub 3-0:1.0: 8 ports detected
[   21.847153] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   21.847186] 8139cp: pci dev 0000:02:03.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   21.847190] 8139cp: Try the "8139too" driver instead.
[   21.849098] 8139too Fast Ethernet driver 0.9.27
[   21.849149] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 18 (level, low) -> IRQ 18
[   21.849824] eth0: RealTek RTL8139 at 0xffffc20000046c00, 00:13:d3:af:0c:9c, IRQ 18
[   21.849827] eth0:  Identified 8139 chip type 'RTL-8101'
[   22.438927] usb 2-3: new full speed USB device using ohci_hcd and address 2
[   24.290023] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   24.294555] ACPI: Thermal Zone [THRM] (59 C)
[   24.644722] Attempting manual resume
[   24.644927] swsusp: Suspend partition has wrong signature?
[   24.665450] kjournald starting.  Commit interval 5 seconds
[   24.665461] EXT3-fs: mounted filesystem with ordered data mode.
[   25.990405] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   29.521400] Adding 586332k swap on /dev/hda5.  Priority:-1 extents:1
[   29.847159] EXT3 FS on hda2, internal journal
[   38.060859] lp: driver loaded but no devices found
[   38.092106] mice: PS/2 mouse device common for all mice
[   38.124744] Real Time Clock Driver v1.12
[   38.138829] ieee1394: Initialized config rom entry `ip1394'
[   38.145576] SCSI subsystem initialized
[   38.150582] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[   38.321597] logips2pp: Detected unknown logitech mouse model 99
[   38.384654] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio2
[   38.875142] ts: Compaq touchscreen protocol output
[   41.219896] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   42.111910] cdrom: open failed.
[   42.784429] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   45.053440] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.062786] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.501539] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   46.911300] Linux Kernel Card Services
[   46.911305]   options:  [pci] [cardbus] [pm]
[   46.923728] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[   46.923747] Yenta: CardBus bridge found at 0000:02:04.0 [1462:0291]
[   47.044485] Yenta: ISA IRQ mask 0x04b8, PCI irq 19
[   47.044489] Socket status: 30000006
[   47.059909] ACPI: PCI Interrupt 0000:02:04.1[B] -> GSI 20 (level, low) -> IRQ 20
[   47.059924] Yenta: CardBus bridge found at 0000:02:04.1 [1462:0291]
[   47.180513] Yenta: ISA IRQ mask 0x04b8, PCI irq 20
[   47.180518] Socket status: 30000006
[   47.339997] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[   47.340031] ACPI: PCI Interrupt 0000:02:04.2[C] -> GSI 21 (level, low) -> IRQ 21
[   47.396249] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fbfff000-fbfff7ff]  Max Packet=[2048]
[   47.481890] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   47.481898] rt2500 1.1.0 CVS 2005/07/10 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[   48.663423] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000d92d88]
[   48.774155] Bluetooth: Core ver 2.7
[   48.774165] NET: Registered protocol family 31
[   48.774167] Bluetooth: HCI device and connection manager initialized
[   48.774182] Bluetooth: HCI socket layer initialized
[   48.778570] Bluetooth: HCI USB driver ver 2.8
[   48.787491] usbcore: registered new driver hci_usb
[   49.279012] input: PC Speaker
[   50.055241] NET: Registered protocol family 17
[  111.192858] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  114.480281] NET: Registered protocol family 10
[  114.480391] Disabled Privacy Extensions on device ffffffff8035a7c0(lo)
[  114.480591] IPv6 over IPv4 tunneling driver
[  116.136742] ACPI: AC Adapter [ADP1] (on-line)
[  116.182829] ACPI: Battery Slot [BAT1] (battery present)
[  116.199003] ACPI: Power Button (FF) [PWRF]
[  116.199028] ACPI: Lid Switch [LID0]
[  116.199035] ACPI: Sleep Button (CM) [SLPB]
[  116.199046] ACPI: Power Button (CM) [PWRB]
[  116.294812] ibm_acpi: ec object not found
[  124.799654] ra0: no IPv6 routers present
[  125.440780] eth0: no IPv6 routers present
[  126.955633] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[  126.964287] powernow-k8:    0 : fid 0x0 (800 MHz), vid 0x13 (1075 mV)
[  126.964293] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc (1250 mV)
[  126.964297] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[  126.964749] cpu_init done, current fid 0xa, vid 0x8
[  126.980284] powernow-k8: ph2 null fid transition 0xa
[  127.337964] Bluetooth: L2CAP ver 2.7
[  127.337970] Bluetooth: L2CAP socket layer initialized
[  127.367789] Bluetooth: HIDP (Human Interface Emulation) ver 1.1
[  127.381801] Bluetooth: RFCOMM ver 1.5
[  127.381810] Bluetooth: RFCOMM socket layer initialized
[  127.381826] Bluetooth: RFCOMM TTY layer initialized
[  157.723589] psmouse.c: Wheel Mouse at isa0060/serio2/input0 lost synchronization, throwing 1 bytes away.
[  181.475583] usb 3-1: new high speed USB device using ehci_hcd and address 3
[  181.517264] hub 3-1:1.0: USB hub found
[  181.517349] hub 3-1:1.0: 1 port detected
[  181.618410] usb 3-1.1: new high speed USB device using ehci_hcd and address 4[  181.737523] Initializing USB Mass Storage driver...
[  181.740539] scsi0 : SCSI emulation for USB Mass Storage devices
[  181.741519] usb-storage: device found at 4
[  181.741522] usb-storage: waiting for device to settle before scanning
[  181.741752] usbcore: registered new driver usb-storage
[  181.741756] USB Mass Storage support registered.
[  183.964910]   Vendor: USB 2.0   Model: Flash Disk        Rev: 1.00
[  183.964919]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  183.968122] usb-storage: device scan complete
[  184.003587] SCSI device sda: 507904 512-byte hdwr sectors (260 MB)
[  184.004922] sda: Write Protect is off
[  184.004926] sda: Mode Sense: 00 26 00 00
[  184.004929] sda: assuming drive cache: write through
[  184.007201] SCSI device sda: 507904 512-byte hdwr sectors (260 MB)
[  184.008536] sda: Write Protect is off
[  184.008539] sda: Mode Sense: 00 26 00 00
[  184.008542] sda: assuming drive cache: write through
[  184.008546]  /dev/scsi/host0/bus0/target0/lun0: p1
[  184.009960] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0kyle@lappyUBUNTU64:~$


---

### Post by ervaringsdeskundige on 2006-05-09
I had the same problem as dvarsam. After reading this thread, I learned how to mount the file system on the USB stick:
$ sudo mount -t vfat /dev/sda1 /mnt/usbstick
But can mounting of a USB stick file vfat file system finally be completely made automatic, (as in Windows...)?

Thanks in advance.

---

### Post by aktiwers on 2006-05-09
I think you guys should start a new threat if you want answers. Im a noob my self so I cant answer, but it will be hard to answer 3 people in the same Topic :)

---

### Post by rcatman on 2006-06-12
I have a Sandisk Micro 256mb. I got mine running immediatly once i read this post. I installed ubuntu hoary 5.04 on my dell inspiron 3200. 

I've installed the server version then a windows manager so i'm mostly working with the console. I'm pretty new to linux so I'm trying to tackle everything in the console. 

My comp is on. I plug in my usb stick, the light flashes, turns off, then turns on permanently. To find where my usb stick was located i typed

fdisk -l

result:
Disk /dev/sda: 256MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders
Unites = cylinders of 512 * 512 = 262144

Device Boot              Start           End              Blocks        Id      System
/dev/sda1                     1            979             250574+      6       FAT16

then i issued the command:
sudo mount /dev/sda1 /mnt/usbstick

*after i created the usbstick folder of course

i list the directory /mnt/usbstick and its mounted perfectly!

---

### Post by rcatman on 2006-06-12
[QUOTE=rcatman]I have a Sandisk Micro 256mb. I got mine running immediatly once i read this post. I installed ubuntu hoary 5.04 on my dell inspiron 3200. 

I've installed the server version then a windows manager so i'm mostly working with the console. I'm pretty new to linux so I'm trying to tackle everything in the console. 

My comp is on. I plug in my usb stick, the light flashes, turns off, then turns on permanently. To find where my usb stick was located i typed

fdisk -l

result:
Disk /dev/sda: 256MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders
Unites = cylinders of 512 * 512 = 262144

Device Boot              Start           End              Blocks        Id      System
/dev/sda1                     1            979             250574+      6       FAT16

then i issued the command:
sudo mount /dev/sda1 /mnt/usbstick

*after i created the usbstick folder of course

i list the directory /mnt/usbstick and its mounted perfectly![/QUOTE]


butnow i dont know how to unmount it haha :confused: 

umount /dev/sda1 reults in the system telling me the device is busy. even if i try to force an unmount. I dont have any files on it open, or am i accessing it. hhhmmm... any ideas?

---

### Post by elemental666 on 2006-06-12
firstly, you don't unmount the /dev file, you unmount the /mnt/usbstick
so run:
umount /mnt/usbstick

if you get the same result see below:
are you in the /mnt/usbstick directory when you try to unmount it?
are you looking at the directory contents in any file managers?
are you accessing the usbstick in any way shape or form?
if your usbstick flashes with access activity, is it flashing?

if you answered no to all those questions try running unmount as root: sudo umount -f /mnt/usbstick

---

