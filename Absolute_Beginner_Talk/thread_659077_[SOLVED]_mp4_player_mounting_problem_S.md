---
title: "[SOLVED] mp4 player mounting problem :S"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by spydon on 2008-01-05
Hi.
My little sisters mp4 player wont automount when I put it in the USB... And it doesn't show up in lsusb :S.
I can't tell which brand it is it just says NORDIC design by lars jensen on the cover.
It doesn't show up in fdisk -l either.
Does anyone have any tips?

---

### Post by jshein on 2008-01-05
For starters, verify that you have the latest pciids installed on your system

$ sudo update-pciids

Then once that has completed, check the output of dmesg after you have plugged in the  USB device, to verify that it is even being seen at all. Please post the last 20 or so lines form dmesg here.

---

### Post by spydon on 2008-01-05
```
[185807.684000] usb-storage: device scan complete
[185807.768000] scsi 9:0:0:0: Direct-Access     SAMSUNG  HD501LJ               PQ: 0 ANSI: 2 CCS
[185807.772000] sd 9:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[185807.772000] sd 9:0:0:0: [sdb] Write Protect is off
[185807.772000] sd 9:0:0:0: [sdb] Mode Sense: 00 38 00 00
[185807.772000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[185807.772000] sd 9:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[185807.776000] sd 9:0:0:0: [sdb] Write Protect is off
[185807.776000] sd 9:0:0:0: [sdb] Mode Sense: 00 38 00 00
[185807.776000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[185807.776000]  sdb: sdb1
[185807.776000] sd 9:0:0:0: [sdb] Attached SCSI disk
[185807.776000] sd 9:0:0:0: Attached scsi generic sg2 type 0
[185807.976000] usb-storage: device scan complete
[185808.028000] scsi 10:0:0:0: Direct-Access     Maxtor   OneTouch II      023d PQ: 0 ANSI: 4
[185808.080000] sd 10:0:0:0: [sdc] 586114704 512-byte hardware sectors (300091 MB)
[185808.136000] sd 10:0:0:0: [sdc] Write Protect is off
[185808.136000] sd 10:0:0:0: [sdc] Mode Sense: 24 00 00 00
[185808.136000] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[185808.196000] sd 10:0:0:0: [sdc] 586114704 512-byte hardware sectors (300091 MB)
[185808.248000] sd 10:0:0:0: [sdc] Write Protect is off
[185808.248000] sd 10:0:0:0: [sdc] Mode Sense: 24 00 00 00
[185808.248000] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[185808.248000]  sdc: sdc1
[185808.272000] sd 10:0:0:0: [sdc] Attached SCSI disk
[185808.272000] sd 10:0:0:0: Attached scsi generic sg3 type 0
[187515.900000] UDF-fs: No VRS found
[187515.936000] ISO 9660 Extensions: Microsoft Joliet Level 3
[187515.952000] ISOFS: changing to secondary root

```

it updated something with the sudo update-pciids and there is the dmesg but it doesn't seem to show up... :S
I shall try on another computer too to see that theres no problem with the USB port or something...

---

### Post by spydon on 2008-01-05
The wire was broken but I had another one and now it works perfectly, thx all(jshein's) :).

---

