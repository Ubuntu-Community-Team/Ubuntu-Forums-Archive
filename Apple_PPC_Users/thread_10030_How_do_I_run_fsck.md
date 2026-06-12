---
title: "How do I run fsck?"
date: 2005-01-04
forum: Apple PPC Users
---

### Post by xico on 2005-01-04
Hello,
I get about 30 error messages during the booting of Ubuntu:

I/O error, dev sda, sector xxxxxxx
Buffer I/O error on device sda
SCSIO: Error on channel0, id 6

I guess it's bad block in the tree. 
Here's my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
/dev/sda3 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 ro,user,noauto 0 0

How do I run fsck? 
Not on a mounted partition!
A running partition can't be unmounted!
Then how? Is there a kernel argument in BootX?


Thanks for helping

Francois

---

### Post by xico on 2005-01-05
Here's my dmesg:

ror, dev sda, sector 8899655
Buffer I/O error on device sda, logical block 8899655
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 48 00 00 38 00 
Info fld=0x87cc48, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899656
Buffer I/O error on device sda, logical block 8899656
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 49 00 00 37 00 
Info fld=0x87cc49, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899657
Buffer I/O error on device sda, logical block 8899657
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 4a 00 00 36 00 
Info fld=0x87cc4a, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899658
Buffer I/O error on device sda, logical block 8899658
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 4b 00 00 35 00 
Info fld=0x87cc4b, Current sda: sense key Medium Error
Additional sense: Unrecovered read error
end_request: I/O error, dev sda, sector 8899659
Buffer I/O error on device sda, logical block 8899659
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 4c 00 00 34 00 
Info fld=0x87cc4c, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899660
Buffer I/O error on device sda, logical block 8899660
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 4d 00 00 33 00 
Info fld=0x87cc4d, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899661
Buffer I/O error on device sda, logical block 8899661
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 4e 00 00 32 00 
Info fld=0x87cc4e, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899662
Buffer I/O error on device sda, logical block 8899662
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 4f 00 00 31 00 
Info fld=0x87cc4f, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899663
Buffer I/O error on device sda, logical block 8899663
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 50 00 00 30 00 
Info fld=0x87cc50, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899664
Buffer I/O error on device sda, logical block 8899664
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 51 00 00 2f 00 
Info fld=0x87cc51, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899665
Buffer I/O error on device sda, logical block 8899665
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 52 00 00 2e 00 
Info fld=0x87cc52, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899666
Buffer I/O error on device sda, logical block 8899666
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 53 00 00 2d 00 
Info fld=0x87cc53, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899667
Buffer I/O error on device sda, logical block 8899667
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 54 00 00 2c 00 
Info fld=0x87cc54, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899668
Buffer I/O error on device sda, logical block 8899668
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 55 00 00 2b 00 
Info fld=0x87cc55, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899669
Buffer I/O error on device sda, logical block 8899669
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 56 00 00 2a 00 
Info fld=0x87cc56, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899670
Buffer I/O error on device sda, logical block 8899670
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 57 00 00 29 00 
Info fld=0x87cc57, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899671
Buffer I/O error on device sda, logical block 8899671
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 58 00 00 28 00 
Info fld=0x87cc58, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899672
Buffer I/O error on device sda, logical block 8899672
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 59 00 00 27 00 
Info fld=0x87cc59, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899673
Buffer I/O error on device sda, logical block 8899673
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 5a 00 00 26 00 
Info fld=0x87cc5a, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899674
Buffer I/O error on device sda, logical block 8899674
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 5b 00 00 25 00 
Info fld=0x87cc5b, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899675
Buffer I/O error on device sda, logical block 8899675
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 5c 00 00 24 00 
Info fld=0x87cc5c, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899676
Buffer I/O error on device sda, logical block 8899676
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 5d 00 00 23 00 
Info fld=0x87cc5d, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899677
Buffer I/O error on device sda, logical block 8899677
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 5e 00 00 22 00 
Info fld=0x87cc5e, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899678
Buffer I/O error on device sda, logical block 8899678
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 5f 00 00 21 00 
Info fld=0x87cc5f, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899679
Buffer I/O error on device sda, logical block 8899679
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 60 00 00 20 00 
Info fld=0x87cc60, Current sda: sense key Medium Error
Additional sense: Unrecovered read error
end_request: I/O error, dev sda, sector 8899680
Buffer I/O error on device sda, logical block 8899680
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 61 00 00 1f 00 
Info fld=0x87cc61, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899681
Buffer I/O error on device sda, logical block 8899681
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 62 00 00 1e 00 
Info fld=0x87cc62, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899682
Buffer I/O error on device sda, logical block 8899682
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 63 00 00 1d 00 
Info fld=0x87cc63, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899683
Buffer I/O error on device sda, logical block 8899683
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 64 00 00 1c 00 
Info fld=0x87cc64, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899684
Buffer I/O error on device sda, logical block 8899684
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 65 00 00 1b 00 
Info fld=0x87cc65, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899685
Buffer I/O error on device sda, logical block 8899685
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 66 00 00 1a 00 
Info fld=0x87cc66, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899686
Buffer I/O error on device sda, logical block 8899686
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 67 00 00 19 00 
Info fld=0x87cc67, Current sda: sense key Medium Error
Additional sense: Unrecovered read error
end_request: I/O error, dev sda, sector 8899687
Buffer I/O error on device sda, logical block 8899687
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 68 00 00 18 00 
Info fld=0x87cc68, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899688
Buffer I/O error on device sda, logical block 8899688
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 69 00 00 17 00 
Info fld=0x87cc69, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899689
Buffer I/O error on device sda, logical block 8899689
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 6a 00 00 16 00 
Info fld=0x87cc6a, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899690
Buffer I/O error on device sda, logical block 8899690
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 6b 00 00 15 00 
Info fld=0x87cc6b, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899691
Buffer I/O error on device sda, logical block 8899691
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 6c 00 00 14 00 
Info fld=0x87cc6c, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899692
Buffer I/O error on device sda, logical block 8899692
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 6d 00 00 13 00 
Info fld=0x87cc6d, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899693
Buffer I/O error on device sda, logical block 8899693
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 6e 00 00 12 00 
Info fld=0x87cc6e, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899694
Buffer I/O error on device sda, logical block 8899694
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 6f 00 00 11 00 
Info fld=0x87cc6f, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899695
Buffer I/O error on device sda, logical block 8899695
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 70 00 00 10 00 
Info fld=0x87cc70, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899696
Buffer I/O error on device sda, logical block 8899696
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 71 00 00 0f 00 
Info fld=0x87cc71, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899697
Buffer I/O error on device sda, logical block 8899697
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 72 00 00 0e 00 
Info fld=0x87cc72, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899698
Buffer I/O error on device sda, logical block 8899698
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 73 00 00 0d 00 
Info fld=0x87cc73, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899699
Buffer I/O error on device sda, logical block 8899699
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 74 00 00 0c 00 
Info fld=0x87cc74, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899700
Buffer I/O error on device sda, logical block 8899700
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 75 00 00 0b 00 
Info fld=0x87cc75, Current sda: sense key Medium Error
ASC=11 ASCQ=c0
end_request: I/O error, dev sda, sector 8899701
Buffer I/O error on device sda, logical block 8899701
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 76 00 00 0a 00 
Info fld=0x87cc76, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899702
Buffer I/O error on device sda, logical block 8899702
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 77 00 00 09 00 
Info fld=0x87cc77, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899703
Buffer I/O error on device sda, logical block 8899703
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 78 00 00 08 00 
Info fld=0x87cc78, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899704
Buffer I/O error on device sda, logical block 8899704
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 79 00 00 07 00 
Info fld=0x87cc79, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899705
Buffer I/O error on device sda, logical block 8899705
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 7a 00 00 06 00 
Info fld=0x87cc7a, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899706
Buffer I/O error on device sda, logical block 8899706
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 7b 00 00 05 00 
Info fld=0x87cc7b, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899707
Buffer I/O error on device sda, logical block 8899707
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 7c 00 00 04 00 
Info fld=0x87cc7c, Current sda: sense key Medium Error
ASC=11 ASCQ=c0
end_request: I/O error, dev sda, sector 8899708
Buffer I/O error on device sda, logical block 8899708
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 7d 00 00 03 00 
Info fld=0x87cc7d, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899709
Buffer I/O error on device sda, logical block 8899709
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 7e 00 00 02 00 
Info fld=0x87cc7e, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899710
Buffer I/O error on device sda, logical block 8899710
scsi0: ERROR on channel 0, id 6, lun 0, CDB: Read (10) 00 00 87 cc 7f 00 00 01 00 
Info fld=0x87cc7f, Current sda: sense key Medium Error
ASC=13 ASCQ=c0
end_request: I/O error, dev sda, sector 8899711
Buffer I/O error on device sda, logical block 8899711
Current sda: sense key No Sense
cdrom: open failed.
ts: Compaq touchscreen protocol output
ieee1394: Initialized config rom entry `ip1394'
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
PCI: Enabling device 0000:00:0f.0 (0014 -> 0016)
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[25]  MMIO=[81801000-818017ff]  Max Packet=[2048]
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000303c000911ef]
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Feb 02 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd: block sizes: ed 64 td 64
USB Universal Host Controller Interface driver v2.2
phy registers:
 0000 0000 0000 0000 0000 0000 0000 0000
 0000 0000 0000 0000 0000 0000 0000 0000
 0000 0000 0000 0000 0000 0000 0000 0000
 0000 0000 0000 0000 0000 0000 0000 0000
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0236384(lo)
IPv6 over IPv4 tunneling driver
divert: not allocating divert_blk for non-ethernet device sit0

---

### Post by ankitmalik on 2005-01-05
What i do is to use Knoppix /other Live CD and scan the unmounted disk!

Simple MEPIS makes it more simpler.

Although I am sure there might be another way to but I am not aware :D

---

### Post by xico on 2005-01-05
I can't use a live CD because my computer is an oldworld one and won't boot out of a non Apple CD (OpenFirmware problem).
Thanks anyway

---

### Post by chascon on 2005-01-29
This is a huge and common misconception.
Yes, you can get old world macs to boot live CDs.  I have the info somewhere on another computer.  But if you're in a jam I know that there is dev at rocklinux irc that makes live CDs for the 608? processor that can tell you how.  Just as on a pc, I believe you have to make a file onto a floppy to tell the mac to boot from the CD.  There is another way too by including said file onto the live CD but devs just don't include this into live CDs.  Anyway, maybe this has changed.

---

### Post by chandakmayank on 2006-08-30
Just try this it solved all my problem.

Under etc director open fstab.

On whichever device u r getting these errors, just change those values at end(from 0 1 or 1 1) to 0 0.

This works , really.
Just post a thanks, if it works for you guys.

---

### Post by chronniff on 2007-03-07
use bonager, it worked for me get it at  [http://www.ubuntuforums.org/showthread.php?t=295262]("http://www.ubuntuforums.org/showthread.php?t=295262")

---

### Post by valuntahr on 2007-12-20
> **chandakmayank said:**
> Just try this it solved all my problem.

Under etc director open fstab.

On whichever device u r getting these errors, just change those values at end(from 0 1 or 1 1) to 0 0.

This works , really.
Just post a thanks, if it works for you guys.

From my understanding of Fstab, what you just described doesn't really fix the problem. It just tells the operating system to ignore that drive whenever it runs fsck during bootup.

---

### Post by stmiller on 2007-12-20
woops dupe post.

---

### Post by stmiller on 2007-12-20
You can boot into single user mode to run fsck. In powerpc Linux, type this at the yaboot prompt:
```

Linux single

```
then fsck away...

---

### Post by allebone on 2008-03-28
to schedule a fsck on next boot, login as root and type:

touchfile fsckforce
reload

(login as root using sudo passwd root, then su)

---

### Post by stream303 on 2008-03-30
Do you mean
```

sudo touch /forcefsck
```

and then rebooting?

---

