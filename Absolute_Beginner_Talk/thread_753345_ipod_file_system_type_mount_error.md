---
title: "ipod file system type mount error"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by PhishingJimi on 2008-04-12
My ipod used to auto-mount correctly when I would plug it in with Amarok open. However I plugged it in yesterday to update for the first time in a few weeks, and it wouldnt mount. the pop-up error i received is as follows:

Cannot mount volume

Unable to mount the volume 'KYLE'S IPOD'

mount:wrong fs type, bad option, bad superblock on /dev/sdd2, missing codepage or helper program, or other error. In some cases useful info is found in syslog -try dmesg | tail or so

Any help on this subject would be greatly appreciated. Please post if further information is required.

Thanks,
PhishingJimi

---

### Post by Capricori on 2008-04-12
Try typing 'dmesg' into a terminal right after plugging it in, post the last few lines of the output up here.

---

### Post by sardion on 2008-04-12
I agree... we need the output of dmesg to know for sure...

If its a "Mac" iPod:
 make sure hfsplus is installed:

dpkg -l | grep hfsplus

aptitude install hfsplus

If its a "windows" ipod:  do the same for vfat

---

### Post by PhishingJimi on 2008-04-13
This is the output from dmesg after I plugged my ipod into the usb port:


[72891.171363] usb 2-3.3: new high speed USB device using ehci_hcd and address 7
[72891.266054] usb 2-3.3: configuration #1 chosen from 2 choices
[72891.266409] scsi8 : SCSI emulation for USB Mass Storage devices
[72891.266435] usb-storage: device found at 7
[72891.266436] usb-storage: waiting for device to settle before scanning
[72896.251129] usb-storage: device scan complete
[72896.251992] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ
: 0 ANSI: 0
[72896.253967] SCSI device sdd: 117210240 512-byte hdwr sectors (60012 MB)
[72896.256597] sdd: Write Protect is off
[72896.256601] sdd: Mode Sense: 68 00 00 08
[72896.256602] sdd: assuming drive cache: write through
[72896.262339] SCSI device sdd: 117210240 512-byte hdwr sectors (60012 MB)
[72896.264721] sdd: Write Protect is off
[72896.264724] sdd: Mode Sense: 68 00 00 08
[72896.264725] sdd: assuming drive cache: write through
[72896.264728]  sdd: sdd1 sdd2
[72896.283668] sd 8:0:0:0: Attached scsi removable disk sdd
[72896.283705] sd 8:0:0:0: Attached scsi generic sg3 type 0
[72897.198143] FAT: Unrecognized mount option "usefree" or missing value

---

