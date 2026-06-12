---
title: "sd cardreader, automount - need help"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by mxsteini on 2007-11-02
Hi there,
I using an external cardreader or an usb-digicam.
Both of them where automounted until 6.10.

The cardreader and the card is correctly detected:
> 
[ 1376.496000] usb-storage: device found at 5
[ 1376.496000] usb-storage: waiting for device to settle before scanning
[ 1381.496000] usb-storage: device scan complete
[ 1381.496000] scsi 3:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[ 1381.504000] scsi 3:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[ 1381.508000] scsi 3:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[ 1381.512000] scsi 3:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[ 1382.084000] SCSI device sdb: 996352 512-byte hdwr sectors (510 MB)
[ 1382.084000] sdb: Write Protect is off
[ 1382.084000] sdb: Mode Sense: 03 00 00 00
[ 1382.084000] sdb: assuming drive cache: write through
[ 1382.092000] SCSI device sdb: 996352 512-byte hdwr sectors (510 MB)
[ 1382.092000] sdb: Write Protect is off
[ 1382.092000] sdb: Mode Sense: 03 00 00 00
[ 1382.092000] sdb: assuming drive cache: write through
[ 1382.092000]  sdb: sdb1
[ 1382.096000] sd 3:0:0:0: Attached scsi removable disk sdb
[ 1382.096000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1382.096000] sd 3:0:0:1: Attached scsi removable disk sdc
[ 1382.096000] sd 3:0:0:1: Attached scsi generic sg3 type 0
[ 1382.100000] sd 3:0:0:2: Attached scsi removable disk sdd
[ 1382.100000] sd 3:0:0:2: Attached scsi generic sg4 type 0
[ 1382.104000] sd 3:0:0:3: Attached scsi removable disk sde
[ 1382.104000] sd 3:0:0:3: Attached scsi generic sg5 type 0


I can mount them by mount or pmount, but it doesn't automount.](*,)
I there anybody out there who has that thing working?
Does anybody know where to report this thing?

---

