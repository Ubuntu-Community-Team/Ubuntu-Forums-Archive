---
title: "Can Burn Cds but having trouble burning DVDs"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by iceman504 on 2007-02-23
i can burn cds fine but when insert a blank dvd it will show up on the desktop and go to the disk manager and click on my dvd writer drive it says no disk is inserted and when using k3b to burn isos or data to a blank dvd i have to use a force option that pops up in k3b.
and recently after using tovid to make a avi to dvd format i try to use the makedvd command and it never recognizes that a disk is in the drive. I dont what the problem is but i didn't have this problem in windows xp so i know the drive isnt the problem.
 and after putting  sudo dmesg | grep -i hdc in a terminal i get this
[17179581.968000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[17179583.664000] hdc: HP DVD Writer 400, ATAPI CD/DVD-ROM drive
[17179584.592000] hdc: ATAPI 40X DVD-ROM CD-R/RW drive, 8192kB Cache, UDMA(33)
[17191196.676000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[17227994.628000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17227994.628000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17227994.628000] end_request: I/O error, dev hdc, sector 0
[17227994.628000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17227994.628000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17227994.628000] end_request: I/O error, dev hdc, sector 0
[17227994.644000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17227994.644000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17227994.644000] end_request: I/O error, dev hdc, sector 0

---

### Post by chggr on 2007-02-23
Did you try to change the DVD's brand you are using?

I had a similar problem and when I switched to another DVD brand the problem was automaticaly solved!

---

### Post by iceman504 on 2007-02-23
yea i tried memorex and i never got it to read those and now im using dynex.... what brand of dvds are you using?

---

