---
title: "[SOLVED] Ran fsck - what do these errors all mean?"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-11
I've got fsck set so I run it manually. Ran it today and /dev/hda1 ok but /dev/hda3 my home partition came up with these, just a sample from dmesg.
```
49, high=6, low=11553053, sector=112216341
[  163.076000] ide: failed opcode was: unknown
[  163.076000] end_request: I/O error, dev hda, sector 112216341
[  163.076000] Buffer I/O error on device hda3, logical block 8651292
[  166.848000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  166.848000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=112216349, high=6, low=11553053, sector=112216349
[  166.848000] ide: failed opcode was: unknown
[  166.848000] end_request: I/O error, dev hda, sector 112216349
[  166.848000] Buffer I/O error on device hda3, logical block 8651293
[  170.892000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  170.892000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=112478329, high=6, low=11815033, sector=112478213
[  170.892000] ide: failed opcode was: unknown
[  170.892000] end_request: I/O error, dev hda, sector 112478213
[  170.892000] Buffer I/O error on device hda3, logical block 8684026
[  174.684000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  174.684000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=112478329, high=6, low=11815033, sector=112478221
[  174.684000] ide: failed opcode was: unknown
[  174.684000] end_request: I/O error, dev hda, sector 112478221
[  174.684000] Buffer I/O error on device hda3, logical block 8684027
[  178.452000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  178.452000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=1124783
```

I ran fsck /dev/hda3 and it asked to ignore errors force rewrite and I said yes. when it finished pass 2-5 I typed exit and here I am. 

Any advice please?

---

### Post by FuturePilot on 2007-10-11
It wasn't mounted was it?

---

### Post by philinux on 2007-10-11
No I typed   sudo touch /forcefsck then rebooted

---

### Post by philinux on 2007-10-11
Ubumpty

---

### Post by Martje_001 on 2007-10-11
Youre hard disk is at some places damaged. I/O means Input/Output which may point out faulty hardware or unclean hardware.

---

### Post by philinux on 2007-10-11
fsck corrected the errors but is there any further steps to take?

---

### Post by philinux on 2007-10-11
Ubumpu

---

### Post by FuturePilot on 2007-10-11
If they have been corrected you're set to go. Usually stuff gets corrupted if it isn't unmounted properly or if a hard reboot is done. Rare, but it can happen.

---

### Post by philinux on 2007-10-11
None of the above happened and its a fresh install after moving to a separate home partition.

And gparted detected no errors a week ago.

---

### Post by FuturePilot on 2007-10-11
It could possibly indicate a failing hard drive. They usually will end up with read and write errors and corrupted data.
Don't quote me on that, I'm not entirely sure if that's the case. Just kind of guessing.

---

### Post by tjagoda on 2007-10-11
Modern Hard Drives have a technology called "SMART."  SMART Hard Drives fix most of these errors before the OS even notices them.  This means, if your OS is detecting hard disk errors over and over again, that the disk is most likely going bad.

SMART reserves a large sector of your hard disk and uses it to replace bad chunks.  Once this fills up, your OS notices the errors and starts to fix them.  

Get a new drive!

---

### Post by philinux on 2007-10-11
Thanks for replies. Is there any way to sort of quarantine these bad areas

---

### Post by philinux on 2007-10-12
Anyone?

---

### Post by tjagoda on 2007-10-12
No.  Your Hard Drive does the quarantine on it's own with it's own cache of reserve sectors.  Your hard drive will in fact hide these errors from you until it starts to run out of reserve sectors, so by the time these start to show up in your OS like they are now, your drive is already late on in it's lifespan.

---

### Post by philinux on 2007-10-12
Ok I installed smartmontools and ran 
```
sudo smartctl -H  /dev/hda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: **PASSED**

```

So it Passed - weird but there are errors reported by this 

```
philcb@philcb-desktop:~$ sudo smartctl -l error /dev/hda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
ATA Error Count: 3711 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 3711 occurred at disk power-on lifetime: 812 hours (33 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 f8 1c ae e0  Error: UNC at LBA = 0x00ae1cf8 = 11410680

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 f5 1c ae e0 00      04:41:55.259  READ DMA EXT
  35 00 18 cf 32 02 e0 00      04:41:51.323  WRITE DMA EXT
  25 00 08 1d 39 d4 e0 00      04:41:59.263  READ DMA EXT
  25 00 08 3f 00 38 e0 00      04:41:59.263  READ DMA EXT
  25 00 08 b7 91 18 e0 00      04:41:59.243  READ DMA EXT

Error 3710 occurred at disk power-on lifetime: 812 hours (33 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 f1 1c ae e0  Error: UNC at LBA = 0x00ae1cf1 = 11410673

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ed 1c ae e0 00      04:41:55.259  READ DMA EXT
  35 00 08 c7 32 02 e0 00      04:41:51.323  WRITE DMA EXT
  35 00 30 97 32 02 e0 00      04:41:51.323  WRITE DMA EXT
  35 00 10 ef 08 16 e0 00      04:41:51.323  WRITE DMA EXT
  35 00 08 67 89 14 e0 00      04:41:47.405  WRITE DMA EXT

Error 3709 occurred at disk power-on lifetime: 812 hours (33 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 f1 1c ae e0  Error: UNC at LBA = 0x00ae1cf1 = 11410673

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ed 1c ae e0 00      04:41:34.716  READ DMA EXT
  35 00 08 dd 01 92 e0 00      04:41:51.323  WRITE DMA EXT
  35 00 10 cd 01 92 e0 00      04:41:51.323  WRITE DMA EXT
  25 00 08 ed 1c ae e0 00      04:41:51.323  READ DMA EXT
  25 00 08 ed 1c ae e0 00      04:41:47.405  READ DMA EXT

Error 3708 occurred at disk power-on lifetime: 812 hours (33 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 f1 1c ae e0  Error: UNC at LBA = 0x00ae1cf1 = 11410673

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ed 1c ae e0 00      04:41:34.716  READ DMA EXT
  25 00 08 ed 1c ae e0 00      04:41:34.715  READ DMA EXT
  35 00 08 8f 32 02 e0 00      04:41:34.715  WRITE DMA EXT
  35 00 08 c5 01 92 e0 00      04:41:34.715  WRITE DMA EXT
  35 00 40 4f 32 02 e0 00      04:41:47.405  WRITE DMA EXT

Error 3707 occurred at disk power-on lifetime: 812 hours (33 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 f1 1c ae e0  Error: UNC at LBA = 0x00ae1cf1 = 11410673

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ed 1c ae e0 00      04:41:34.716  READ DMA EXT
  35 00 08 8f 32 02 e0 00      04:41:34.715  WRITE DMA EXT
  35 00 08 c5 01 92 e0 00      04:41:34.715  WRITE DMA EXT
  35 00 40 4f 32 02 e0 00      04:41:34.715  WRITE DMA EXT
  35 00 10 b5 01 92 e0 00      04:41:34.714  WRITE DMA EXT
```

Now they were generated because I ran badblocks and it found some!
I have a feeling that the bad bits are currently not in use because I dont get any errors in /var/log/messages unless I run fsck or badblocks.

---

### Post by philinux on 2007-10-12
Solved - Check it with seatools and it reports 99 errors. But the aren't in a region used they are free space so I'll just carry on as it passed smartmontools. Just wont run fsck on it.

---

### Post by tjagoda on 2007-10-25
Thats a bad idea.

---

