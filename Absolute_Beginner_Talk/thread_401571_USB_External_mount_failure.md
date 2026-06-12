---
title: "USB External mount failure"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by lizardbliz420 on 2007-04-04
my external hard drive (fat32) won't mount after upgrading to fiesty. today i tried to mount it on a windows computer and it mounted. I believe that it is showing up as a cd drive as i have an extra one listed that when i tried to mount failed.

in another thread it told me to look for error messages and here they are

```
bradtatorship@bradtatorship:~$ grep -iw usb /var/log/messages
Apr  4 09:43:58 bradtatorship kernel: [    3.000000] usbcore: registered new device driver usb
Apr  4 09:43:58 bradtatorship kernel: [    3.000000] USB Universal Host Controller Interface driver v3.0
Apr  4 09:43:58 bradtatorship kernel: [    3.000000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr  4 09:43:58 bradtatorship kernel: [    3.000000] usb usb1: configuration #1 chosen from 1 choice
Apr  4 09:43:58 bradtatorship kernel: [    3.000000] hub 1-0:1.0: USB hub found
Apr  4 09:43:58 bradtatorship kernel: [    3.104000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr  4 09:43:58 bradtatorship kernel: [    3.104000] usb usb2: configuration #1 chosen from 1 choice
Apr  4 09:43:58 bradtatorship kernel: [    3.104000] hub 2-0:1.0: USB hub found
Apr  4 09:43:58 bradtatorship kernel: [    3.208000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr  4 09:43:58 bradtatorship kernel: [    3.208000] usb usb3: configuration #1 chosen from 1 choice
Apr  4 09:43:58 bradtatorship kernel: [    3.208000] hub 3-0:1.0: USB hub found
Apr  4 09:43:58 bradtatorship kernel: [    3.312000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr  4 09:43:58 bradtatorship kernel: [    3.312000] usb usb4: configuration #1 chosen from 1 choice
Apr  4 09:43:58 bradtatorship kernel: [    3.312000] hub 4-0:1.0: USB hub found
Apr  4 09:43:58 bradtatorship kernel: [    3.416000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Apr  4 09:43:58 bradtatorship kernel: [    3.420000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  4 09:43:58 bradtatorship kernel: [    3.420000] usb usb5: configuration #1 chosen from 1 choice
Apr  4 09:43:58 bradtatorship kernel: [    3.420000] hub 5-0:1.0: USB hub found
Apr  4 14:47:14 bradtatorship kernel: [18278.424000] usb 5-1: new high speed USB device using ehci_hcd and address 2
Apr  4 14:47:15 bradtatorship kernel: [18279.040000] usb 5-1: configuration #1 chosen from 1 choice
Apr  4 14:47:16 bradtatorship kernel: [18280.748000] Initializing USB Mass Storage driver...
Apr  4 14:47:16 bradtatorship kernel: [18280.748000] scsi2 : SCSI emulation for USB Mass Storage devices
Apr  4 14:47:16 bradtatorship kernel: [18280.748000] usbcore: registered new interface driver usb-storage
Apr  4 14:47:16 bradtatorship kernel: [18280.748000] USB Mass Storage support registered.
Apr  4 14:48:30 bradtatorship kernel: [18354.288000] usb 5-1: USB disconnect, address 2
Apr  4 14:48:36 bradtatorship kernel: [18360.064000] usb 5-1: new high speed USB device using ehci_hcd and address 3
Apr  4 14:48:36 bradtatorship kernel: [18360.196000] usb 5-1: configuration #1 chosen from 1 choice
Apr  4 14:48:36 bradtatorship kernel: [18360.200000] scsi3 : SCSI emulation for USB Mass Storage devices
Apr  4 14:56:12 bradtatorship kernel: [    2.988000] usbcore: registered new device driver usb
Apr  4 14:56:12 bradtatorship kernel: [    2.988000] USB Universal Host Controller Interface driver v3.0
Apr  4 14:56:12 bradtatorship kernel: [    2.988000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr  4 14:56:12 bradtatorship kernel: [    2.988000] usb usb1: configuration #1 chosen from 1 choice
Apr  4 14:56:12 bradtatorship kernel: [    2.988000] hub 1-0:1.0: USB hub found
Apr  4 14:56:12 bradtatorship kernel: [    3.092000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr  4 14:56:12 bradtatorship kernel: [    3.092000] usb usb2: configuration #1 chosen from 1 choice
Apr  4 14:56:12 bradtatorship kernel: [    3.092000] hub 2-0:1.0: USB hub found
Apr  4 14:56:12 bradtatorship kernel: [    3.196000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr  4 14:56:12 bradtatorship kernel: [    3.196000] usb usb3: configuration #1 chosen from 1 choice
Apr  4 14:56:12 bradtatorship kernel: [    3.196000] hub 3-0:1.0: USB hub found
Apr  4 14:56:12 bradtatorship kernel: [    3.300000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr  4 14:56:12 bradtatorship kernel: [    3.300000] usb usb4: configuration #1 chosen from 1 choice
Apr  4 14:56:12 bradtatorship kernel: [    3.300000] hub 4-0:1.0: USB hub found
Apr  4 14:56:12 bradtatorship kernel: [    3.332000] usb 1-1: new full speed USB device using uhci_hcd and address 2
Apr  4 14:56:12 bradtatorship kernel: [    3.496000] usb 1-1: configuration #1 chosen from 1 choice
Apr  4 14:56:12 bradtatorship kernel: [    3.512000] Initializing USB Mass Storage driver...
Apr  4 14:56:12 bradtatorship kernel: [    3.512000] scsi2 : SCSI emulation for USB Mass Storage devices
Apr  4 14:56:12 bradtatorship kernel: [    3.512000] usbcore: registered new interface driver usb-storage
Apr  4 14:56:12 bradtatorship kernel: [    3.512000] USB Mass Storage support registered.
Apr  4 14:56:12 bradtatorship kernel: [    3.984000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Apr  4 14:56:12 bradtatorship kernel: [    3.988000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  4 14:56:12 bradtatorship kernel: [    3.988000] usb usb5: configuration #1 chosen from 1 choice
Apr  4 14:56:12 bradtatorship kernel: [    3.988000] hub 5-0:1.0: USB hub found
Apr  4 14:56:12 bradtatorship kernel: [    4.332000] usb 5-1: new high speed USB device using ehci_hcd and address 2
Apr  4 14:56:12 bradtatorship kernel: [    4.464000] usb 5-1: configuration #1 chosen from 1 choice
Apr  4 14:56:12 bradtatorship kernel: [    4.464000] scsi3 : SCSI emulation for USB Mass Storage devices
Apr  4 14:56:12 bradtatorship kernel: [    4.464000] usb 1-1: USB disconnect, address 2

```

please help<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by chalex on 2007-04-04
I'm not very familiar with these messages, but I don't see anything wrong.

After you connect it and you see the messages in the log, what happens if you do "sudo fdisk -l".  that command should list the partition information on all the disks in your system. does this disk show up?

---

### Post by lizardbliz420 on 2007-04-04
thanks for the help

it shows up as this
```
bradtatorship@bradtatorship:~$ sudo fdisk -l
Password:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4717    37889271   83  Linux
/dev/sda2            4718        4864     1180777+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)
bradtatorship@bradtatorship:~$ pmount
Usage:

```

---

### Post by lizardbliz420 on 2007-04-05
could someone please help me:confused:

---

