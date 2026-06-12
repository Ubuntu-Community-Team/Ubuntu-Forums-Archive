---
title: "USB Flash Drive Won't Mount"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Tamise on 2007-10-23
I'm trying to mount a usb clip drive that worked fine under Feisty, but suddenly doesn't work on Gutsy.

I plug it in, and it gives me a warning box saying unable to mount.  When I go the terminal and hit dmesg, I get the following.

[ 1173.798377] usb 1-1: new full speed USB device using ohci_hcd and address 4
[ 1174.005589] usb 1-1: configuration #1 chosen from 1 choice
[ 1174.008641] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1174.008810] usb-storage: device found at 4
[ 1174.008813] usb-storage: waiting for device to settle before scanning
[ 1179.001317] usb-storage: device scan complete
[ 1179.005312] scsi 5:0:0:0: Direct-Access     BUFFALO  ClipDrive        2.00 PQ: 0 ANSI: 2
[ 1180.166910] ready
[ 1180.170904] SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
[ 1180.174892] sdb: Write Protect is off
[ 1180.174896] sdb: Mode Sense: 03 00 00 00
[ 1180.174898] sdb: assuming drive cache: write through
[ 1180.189069] SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
[ 1180.193059] sdb: Write Protect is off
[ 1180.193066] sdb: Mode Sense: 03 00 00 00
[ 1180.193069] sdb: assuming drive cache: write through
[ 1180.193074]  sdb: sdb1
[ 1180.201151] sd 5:0:0:0: Attached scsi removable disk sdb
[ 1180.201201] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 1181.129994] FAT: Unrecognized mount option "usefree" or missing value

I did sudo rmmod ehci_hcd, but that didn't seem to help.

Any ideas?

I really need to be able to use the drive as the computer has no cd drive on it, and it's a pain to have to boot into Windows to copy something off the drive.

Thanks.

---

### Post by realvz on 2007-10-23
reinstall HAL from synaptics...
if doesnt work then
reboot...try usb again...
still doesnt work
reboot...reinstall HAL from synaptics...try USB

---

### Post by Tamise on 2007-10-24
Hmm - I tried that a couple of times and it didn't work.  Is there anything else that could cause the problem?

Thanks.

---

