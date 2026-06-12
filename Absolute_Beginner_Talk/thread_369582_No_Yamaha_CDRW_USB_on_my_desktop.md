---
title: "No Yamaha CDRW USB on my desktop"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by housekid on 2007-02-24
Ubuntu 6.06
HELP!!!!!!!!!

No Yamaha CDRW USB on my desktop, I can not get to my backup files on my cdrw disk!
All of my important files from gates crash-n-crash-somemore system are on these disks.

I turned everything on when I installed Ubuntu and as you can see blow when I run "lsusb"
my Yamaha cdrw(USB) is mounted. I have inserted many of my old backup disk into the drive hoping
that would cause it to load but nothing has worked so far.

dal@jar-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 005: ID 0499:6001 Yamaha Corp. CRW2200UX Lightspeed 2 External CD-RW Drive
Bus 003 Device 002: ID 059b:0075 Iomega Corp.
Bus 003 Device 004: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 003 Device 003: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

I also have an external Iomega USB dive and it is mounted and on the desktop.
I don't understand why it will do one USB drive and not the other?

I've search the Ubuntu forum but have not found anything that will help.

If someone would please show me from scratch how to get the Yamaha CDRW USB working and
on the desktop, I will be very thankful?
 I Thank You in advance!

---

### Post by n8bounds on 2007-02-24
Open Nautilus (go to your homefolder or something) and Go to the File System (root or / ) and look for a media folder....in there should be your cd rom...

---

### Post by housekid on 2007-02-24
> **n8bounds said:**
> Open Nautilus (go to your homefolder or something) and Go to the File System (root or / ) and look for a media folder....in there should be your cd rom...

I found media and I opened it and clicked on cdrom0 and it shows that it is "Empty".
I have a disk in the drive, but it's not showing up.

---

### Post by n8bounds on 2007-02-24
Checking lsusb is good troubleshooting.  Tell me, have you booted with the usb cdrom on and attached already, or only done so AFTER its all booted up and logged in?

Do this also.  Turn off then unplug the cdrom.  View your /var/log/messages file...maybe save a copy in your homefolder.  Then connect and power on the cdrom.  Wait maybe 5 seconds and view the same file again.  There should be logs therein concerning your device.  Anything weird?

---

### Post by housekid on 2007-02-25
I have rebooted many times with usb cdrom turned on and attached,
I have turned it off and on after bootup many times to see what will work.

I turned the unit off and unplugged it, then I opened /var/log/messages file and saved a copy,
I waited the 5 seconds and then reopened the file and like the first time I don't understand
all that it is showing but this is what was at the bottom:


Feb 24 20:32:35 localhost -- MARK --
Feb 24 20:52:35 localhost -- MARK --
Feb 24 21:00:03 localhost kernel: [ 5343.606997] usb 3-2.2: USB disconnect, address 5
Feb 24 21:11:53 localhost kernel: [ 6053.150390] usb 3-2.2: new full speed USB device using uhci_hcd and address 6
Feb 24 21:11:53 localhost kernel: [ 6053.244290] usb 3-2.2: not running at top speed; connect to a high speed hub
Feb 24 21:11:53 localhost kernel: [ 6053.255780] scsi2 : SCSI emulation for USB Mass Storage devices
Feb 24 21:11:58 localhost kernel: [ 6058.255821]   Vendor: YAMAHA    Model: CRW2200E          Rev: 1.0D
Feb 24 21:11:58 localhost kernel: [ 6058.255913]   Type:   CD-ROM                             ANSI SCSI revision: 02
Feb 24 21:11:58 localhost kernel: [ 6058.325677] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Feb 24 21:11:58 localhost kernel: [ 6058.326199] sr 2:0:0:0: Attached scsi generic sg1 type 5

---

