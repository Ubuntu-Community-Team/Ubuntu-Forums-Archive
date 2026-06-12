---
title: "Lost iPod / automount problem"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by jcconnor on 2007-06-05
A couple of days ago I could simply connect an iPod into the USB port on my Edgy system and it would automount and I could use Amarok to put tracks on it.

Today, when I plugged it in the system recognizes it but it doesn't automount and Amarok and gtkpod don't see it.

When I run dmesg I get this:

> [17179688.528000] usb 4-6: new high speed USB device using ehci_hcd and address 2
[17179688.664000] usb 4-6: configuration #1 chosen from 2 choices
[17179688.800000] usbcore: registered new driver libusual
[17179688.856000] Initializing USB Mass Storage driver...
[17179688.860000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179688.860000] usbcore: registered new driver usb-storage
[17179688.860000] USB Mass Storage support registered.
[17179688.860000] usb-storage: device found at 2
[17179688.860000] usb-storage: waiting for device to settle before scanning
[17179693.860000] usb-storage: device scan complete
[17179693.864000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17179693.864000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179693.912000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17179693.916000] sda: Write Protect is off
[17179693.916000] sda: Mode Sense: 68 00 00 08
[17179693.916000] sda: assuming drive cache: write through
[17179693.916000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17179693.920000] sda: Write Protect is off
[17179693.920000] sda: Mode Sense: 68 00 00 08
[17179693.920000] sda: assuming drive cache: write through
[17179693.920000]  sda: sda1 sda2
[17179693.924000] sd 0:0:0:0: Attached scsi removable disk sda
[17179693.964000] sd 0:0:0:0: Attached scsi generic sg0 type 0

and lsusb says:

> Bus 004 Device 002: ID 05ac:120a Apple Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Any ideas as to why it won't automount any longer??

---

### Post by Wake Rider on 2007-06-05
I don't know why it won't auto-mount but you could try something like this with the command line

First put a folder called ipod into media

Then

sudo mount /dev/sda2 /media/ipod

to unmount

sudo umount /media/ipod

Hope this helps.

---

### Post by jcconnor on 2007-06-05
Thanks.

I had seen some those commands but had heard that it created problems with Amarok and gtkpod recognizing the iPod correctly.  I was hoping for some other command.

Thanks again!

---

