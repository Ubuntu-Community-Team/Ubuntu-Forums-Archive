---
title: "mounting ipod"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by geckorock69 on 2007-02-27
This is my first post.

Having installed Ubuntu 6.10 on an HP dv6130us, I read the fine manuals (forums and wiki) and managed to get wireless working with network-manager and screen resolution resolved with the 915resolution package. I felt fairly accomplished until I plugged in my iPod.

I have a 2nd gen nano which I plugged into the usb port. The system recognizes the iPod but doesn't do anything with it nor show it in the Places menu.

The following is from *dmesg*:

> [17190587.776000] usb 5-1: new high speed USB device using ehci_hcd and address 7
[17190587.908000] usb 5-1: configuration #1 chosen from 2 choices
[17190587.908000] scsi7 : SCSI emulation for USB Mass Storage devices
[17190587.908000] usb-storage: device found at 7
[17190587.908000] usb-storage: waiting for device to settle before scanning
[17190592.908000] usb-storage: device scan complete
[17190592.908000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17190592.908000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17190592.912000] SCSI device sdb: 3964928 2048-byte hdwr sectors (8120 MB)
[17190592.912000] sdb: Write Protect is off
[17190592.912000] sdb: Mode Sense: 68 00 00 08
[17190592.912000] sdb: assuming drive cache: write through
[17190592.916000] SCSI device sdb: 3964928 2048-byte hdwr sectors (8120 MB)
[17190592.916000] sdb: Write Protect is off
[17190592.916000] sdb: Mode Sense: 68 00 00 08
[17190592.916000] sdb: assuming drive cache: write through
[17190592.916000]  sdb: sdb1 sdb2
[17190592.920000] sd 7:0:0:0: Attached scsi removable disk sdb
[17190592.920000] sd 7:0:0:0: Attached scsi generic sg1 type 0

Any help?

---

### Post by Pelham123 on 2007-02-27
This worked for me

[http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)

Enjoy!

---

### Post by geckorock69 on 2007-02-27
Why would an iPod not automount?

---

### Post by mosiac on 2007-02-27
When I plugged my ipod into my new ubuntu install (Edgy) it automounted but only stuff like contacts and calendar and the like, I am using Amarok to do stuff with music for it.

---

### Post by nonewmsgs on 2007-02-27
what is the best way to transfer the songs from the ipod to the hard disk?  i transfered all my songs over but they are all 4 letter names + the mp3 extension.  some of the id tags seem corrupt.  is there a better way to transfer them to my computer?

---

### Post by mosiac on 2007-02-27
Which program were you using to view what songs you had on your Ipod?  Also were you using Itunes before you started using this program?

---

### Post by nonewmsgs on 2007-03-05
i was just using file system.  it automounted like a cd on the desktop.

---

