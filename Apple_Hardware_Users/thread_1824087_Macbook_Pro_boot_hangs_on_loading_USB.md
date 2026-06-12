---
title: "Macbook Pro boot hangs on loading USB"
date: 2011-08-13
forum: Apple Hardware Users
---

### Post by erLin on 2011-08-13
Hi,

I recently bought a MacBook pro 2.2 and installed ubuntu on it.
It works really fine on Lucid, most known problems are fixed now.
But the boot process takes very long and I already discovered it hangs on loading the finest USB-port driver. 

Any ideas for how to fix this problem?

dmesg | less:
...
[    0.897093] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.029464] usb 1-4: configuration #1 chosen from 1 choice
[    1.144551] EXT4-fs (sda4): mounted filesystem with ordered data mode
[    1.492089] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    1.678576] usb 2-2: configuration #1 chosen from 1 choice
[    1.924054] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    2.102969] usb 4-2: configuration #1 chosen from 1 choice
[    2.156453] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0019e3fffe77e024]
[    2.400051] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    2.580243] usb 5-1: configuration #1 chosen from 1 choice
[    2.583142] hub 5-1:1.0: USB hub found
[    2.585091] hub 5-1:1.0: 3 ports detected
[    2.865104] usb 5-1.1: new full speed USB device using uhci_hcd and address 3
[    2.998235] usb 5-1.1: configuration #1 chosen from 1 choice
[    3.077101] usb 5-1.2: new full speed USB device using uhci_hcd and address 4
[    3.199240] usb 5-1.2: configuration #1 chosen from 1 choice
[    3.277103] usb 5-1.3: new full speed USB device using uhci_hcd and address 5
[    3.397232] usb 5-1.3: configuration #1 chosen from 1 choice
[   32.549314] udev: starting version 151
...

thanks

---

