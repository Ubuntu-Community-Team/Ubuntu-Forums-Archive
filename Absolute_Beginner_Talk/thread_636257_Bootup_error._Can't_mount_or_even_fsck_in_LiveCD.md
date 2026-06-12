---
title: "Bootup error. Can't mount or even fsck in LiveCD"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by corney91 on 2007-12-09
Hi,
The harddrive on my brother's laptop has stopped working. 
To start with, the force fsck would stop half-way through, and wouldn't boot. But booting into the LiveCD and running sudo e2fsck /dev/sda3 would work and then allow you to load up normally. This process would have to be repeated everytime the force fsck occured.

But now it won't boot at all. After the GRUB, it says:'Error 25: DIsk read error, press any key to continue...'
And fsck:
```
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda3
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda3: Attempt to read block from filesystem resulted in short read while reading block 1545

/dev/sda3: Attempt to read block from filesystem resulted in short read reading journal superblock

e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sda3

```

I've searched around and tried many options to fsck, but it cacn never finish.
I found this thread:[http://ubuntuforums.org/showthread.php?t=490683]("http://ubuntuforums.org/showthread.php?t=490683"), which seems to be a similar problem but can't seem to fix the problem with test disk or fsck and I don't know how to dd.
Has anyone got any ideas?

EDIT: /dev/sda3 is the /home, and /dev/sda2 is root
EDIT2: I think this may be from fscking while mounted...

---

### Post by CCNA_student on 2007-12-09
My guess is that you have a bad hard drive. When was the hard drive last working?

---

### Post by corney91 on 2007-12-09
> **CCNA_student said:**
> My guess is that you have a bad hard drive. When was the hard drive last working?

Well, the force fsck stopped working quite a bit ago (before gutsy release) and I thought it may just be a bug because it worked from LiveCD. So, I thought I'd install gutsy on it and that would work (never got round to doing this). But this has only happened and recently. It's pretty new and it hasn't been dropped (at least not to my knowledge:p)

---

### Post by Hospadar on 2007-12-09
you may just have some really nasty corruption issues, are you able to mount the drive and read it from a livecd?

If so, I think your best option may be to recover essential data with a livecd, and then try re-installing.  if the re-install fails, I would bet you have a bad drive.  If the re-install works well, probably there was just some filesystem corruption that was cleared up by the re-format

---

### Post by corney91 on 2007-12-09
> **Hospadar said:**
> you may just have some really nasty corruption issues, are you able to mount the drive and read it from a livecd?

If so, I think your best option may be to recover essential data with a livecd, and then try re-installing.  if the re-install fails, I would bet you have a bad drive.  If the re-install works well, probably there was just some filesystem corruption that was cleared up by the re-format

That was my first instinct, but I can't read it at all. 
Is there any way to fix the corruption, or someway to ignore the corrupt bit?

---

### Post by corney91 on 2007-12-10
Bump

---

### Post by corney91 on 2007-12-11
Anyone?

---

### Post by corney91 on 2007-12-12
Has no-one got any ideas?
Can I not retrieve anything at all?

---

### Post by philinux on 2007-12-12
sudo fsck -v /dev/sda3

if it asks to rewrite a bad bit just hit the y key.

The -v means be verbose thats all.

---

### Post by dstew on 2007-12-12
The thread you posted before has some ideas. The command```
sudo mke2fs -n /dev/sda3
```should list the backup superblocks. You then use a backup superblock number in the command```
sudo e2fsck -b 32768 /dev/sda3
```to try to recover the file system. Of course, substitute a correct backup superblock number for 32768 in the above command.

---

### Post by corney91 on 2007-12-12
> **philinux said:**
> sudo fsck -v /dev/sda3

if it asks to rewrite a bad bit just hit the y key.

The -v means be verbose thats all.
> **dstew said:**
> The thread you posted before has some ideas. The command```
sudo mke2fs -n /dev/sda3
```should list the backup superblocks. You then use a backup superblock number in the command```
sudo e2fsck -b 32768 /dev/sda3
```to try to recover the file system. Of course, substitute a correct backup superblock number for 32768 in the above command.

Thanks but both of these result in the original error message:(
Does this mean all the 'journal superblocks' (dunno what they are) are corrupt?

---

### Post by psusi on 2007-12-12
It sounds like the drive is hosed.  Boot from the live cd and try this:

sudo apt-get install smartmontools
sudo smartctl -a /dev/sda

Post the output and that will give us a better idea of the drive's status.

---

### Post by corney91 on 2007-12-12
> **psusi said:**
> It sounds like the drive is hosed.  Boot from the live cd and try this:

sudo apt-get install smartmontools
sudo smartctl -a /dev/sda

Post the output and that will give us a better idea of the drive's status.

Here we go:
```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.2 series
Device Model:     ST9120821AS
Serial Number:    5PL4MXLK
Firmware Version: 7.24
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Dec 12 22:43:33 2007 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 ( 426) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  68) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0002   095   095   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   100   100   020    Pre-fail  Always       -       566
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   073   060   030    Pre-fail  Always       -       24641313
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1141
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   100   100   020    Pre-fail  Always       -       867
187 Unknown_Attribute       0x0032   001   001   000    Old_age   Always       -       1076
189 Unknown_Attribute       0x003a   098   098   000    Old_age   Always       -       2
190 Temperature_Celsius     0x0022   062   039   045    Old_age   Always   In_the_past 639631398
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       654
193 Load_Cycle_Count        0x0032   085   085   000    Old_age   Always       -       30801
194 Temperature_Celsius     0x0022   038   061   000    Old_age   Always       -       38 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   087   049   000    Old_age   Always       -       110770989
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       4
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       4
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 2050 (device log contains only the most recent five errors)
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

Error 2050 occurred at disk power-on lifetime: 1140 hours (47 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d5 b3 ee e0 00      00:30:36.691  READ DMA
  ec 00 00 00 00 00 a0 00      00:30:34.461  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:30:34.453  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:30:34.441  IDENTIFY DEVICE
  c8 00 08 d5 b3 ee e0 00      00:30:34.436  READ DMA

Error 2049 occurred at disk power-on lifetime: 1140 hours (47 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d5 b3 ee e0 00      00:30:36.691  READ DMA
  ec 00 00 00 00 00 a0 00      00:30:34.461  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:30:34.453  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:30:34.441  IDENTIFY DEVICE
  c8 00 08 d5 b3 ee e0 00      00:30:34.436  READ DMA

Error 2048 occurred at disk power-on lifetime: 1140 hours (47 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d5 b3 ee e0 00      00:30:27.626  READ DMA
  ec 00 00 00 00 00 a0 00      00:30:34.461  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:30:34.453  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:30:34.441  IDENTIFY DEVICE
  c8 00 08 d5 b3 ee e0 00      00:30:34.436  READ DMA

Error 2047 occurred at disk power-on lifetime: 1140 hours (47 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d5 b3 ee e0 00      00:30:27.626  READ DMA
  ec 00 00 00 00 00 a0 00      00:30:27.616  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:30:23.215  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:30:23.208  IDENTIFY DEVICE
  c8 00 08 d5 b3 ee e0 00      00:30:23.195  READ DMA

Error 2046 occurred at disk power-on lifetime: 1140 hours (47 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d5 b3 ee e0 00      00:30:27.626  READ DMA
  ec 00 00 00 00 00 a0 00      00:30:27.616  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:30:23.215  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:30:23.208  IDENTIFY DEVICE
  c8 00 08 d5 b3 ee e0 00      00:30:23.195  READ DMA

SMART Self-test log structure revision number 1

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


```

Surprisingly, I can't make any sense of this:-P
Does it help?

---

### Post by psusi on 2007-12-12
Hrm... the drive itself looks ok from that, but it shows there have been several errors communicating with it.  Try this:

sudo dd if=/dev/sda3 of=/dev/null bs=1024 count=1024

If you get errors from that, paste the output of dmesg, or at least the last few lines of it.

Also if you want to perform a thorough test of the disk to be sure it isn't damaged, do smartctl -t long /dev/sda, then give it about an hour and a half to complete ( it runs in the background ) and then post the output of smartctl -a /dev/sda again.

---

### Post by dstew on 2007-12-13
Once you have entered the **sudo mke2fs -n /dev/sda3** command, you should have a list of backup superblocks. You enter these one by one into the **sudo e2fsck -b *block_number* /dev/sda3** command. You will get the error message each time you enter the number of a bad block, but hopefully you will eventually find a good one. Did you try a lot of block numbers, or only the first one?

It is good to do the **smartctl** checks if you are having disk problems, However, smartctl mainly checks for physical disk problems, but it cannot detect a corrupt file system. You have to use the **fsck** type of programs for that.

---

### Post by psusi on 2007-12-13
You do NOT want to run fsck until you are sure that there are no other problems, or it will likely just foul things up even worse.  

You should really never need to use a backup superblock because having JUST the superblock destroyed is very, very rare.  

I suspect this is a cable problem causing errors accessing the disk.

---

### Post by corney91 on 2007-12-13
> **psusi said:**
> 
sudo dd if=/dev/sda3 of=/dev/null bs=1024 count=1024


```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda3 of=/dev/null bs=1024 count=1024
1024+0 records in
1024+0 records out
1048576 bytes (1.0 MB) copied, 0.394966 seconds, 2.7 MB/s

```

There are no errors in dmesg...

I've ran fsck quite alot. Will this make it worse?

I've just ran sudo smartctl -t long /dev/sda

---

### Post by psusi on 2007-12-13
As long as you don't have fsck try to fix things it can't make them worse.  This is very strange though because it complained that it couldn't access parts of the disk, but dd doesn't have any trouble.  Looks like the disk is fine, so try another sudo fdisk -f -n /dev/sda3, and paste the output with the last few lines of dmesg if it fails.

---

### Post by corney91 on 2007-12-13
> **psusi said:**
> As long as you don't have fsck try to fix things it can't make them worse.  This is very strange though because it complained that it couldn't access parts of the disk, but dd doesn't have any trouble.  Looks like the disk is fine, so try another sudo fdisk -f -n /dev/sda3, and paste the output with the last few lines of dmesg if it fails.

The fdisk man page doesn't have any -n or -f options in it. Do you mean fsck?
That failed dmesg output was:
```
[  516.248000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  516.248000] ata1.00: (BMDMA stat 0x5)
[  516.248000] ata1.00: cmd c8/00:01:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 512 in
[  516.248000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  516.288000] ata1.00: configured for UDMA/100
[  516.288000] ata1: EH complete
[  518.520000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  518.520000] ata1.00: (BMDMA stat 0x5)
[  518.520000] ata1.00: cmd c8/00:01:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 512 in
[  518.520000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  518.556000] ata1.00: configured for UDMA/100
[  518.556000] ata1: EH complete
[  520.784000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  520.784000] ata1.00: (BMDMA stat 0x5)
[  520.784000] ata1.00: cmd c8/00:01:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 512 in
[  520.784000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  520.820000] ata1.00: configured for UDMA/100
[  520.820000] ata1: EH complete
[  523.044000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  523.044000] ata1.00: (BMDMA stat 0x5)
[  523.044000] ata1.00: cmd c8/00:01:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 512 in
[  523.044000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  523.072000] ata1.00: configured for UDMA/100
[  523.072000] ata1: EH complete
[  525.296000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  525.296000] ata1.00: (BMDMA stat 0x5)
[  525.296000] ata1.00: cmd c8/00:01:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 512 in
[  525.296000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  525.324000] ata1.00: configured for UDMA/100
[  525.324000] ata1: EH complete
[  529.720000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  529.720000] ata1.00: (BMDMA stat 0x5)
[  529.720000] ata1.00: cmd c8/00:01:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 512 in
[  529.720000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  529.756000] ata1.00: configured for UDMA/100
[  529.756000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  529.756000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  529.756000] Descriptor sense data with sense descriptors (in hex):
[  529.756000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  529.756000]         00 ee b3 d5 
[  529.756000] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  529.756000] end_request: I/O error, dev sda, sector 15643605
[  529.756000] Buffer I/O error on device sda3, logical block 12360
[  529.756000] ata1: EH complete
[  534.144000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  534.144000] ata1.00: (BMDMA stat 0x5)
[  534.144000] ata1.00: cmd c8/00:07:d6:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 3584 in
[  534.144000]          res 51/40:00:d6:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  534.188000] ata1.00: configured for UDMA/100
[  534.188000] ata1: EH complete
[  538.572000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  538.572000] ata1.00: (BMDMA stat 0x5)
[  538.572000] ata1.00: cmd c8/00:07:d6:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 3584 in
[  538.572000]          res 51/40:00:d6:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  538.616000] ata1.00: configured for UDMA/100
[  538.616000] ata1: EH complete
[  540.832000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  540.832000] ata1.00: (BMDMA stat 0x5)
[  540.832000] ata1.00: cmd c8/00:07:d6:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 3584 in
[  540.832000]          res 51/40:00:d6:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  540.860000] ata1.00: configured for UDMA/100
[  540.860000] ata1: EH complete
[  545.248000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  545.248000] ata1.00: (BMDMA stat 0x5)
[  545.248000] ata1.00: cmd c8/00:07:d6:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 3584 in
[  545.248000]          res 51/40:00:d6:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  545.292000] ata1.00: configured for UDMA/100
[  545.292000] ata1: EH complete
[  549.684000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  549.684000] ata1.00: (BMDMA stat 0x5)
[  549.684000] ata1.00: cmd c8/00:07:d6:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 3584 in
[  549.684000]          res 51/40:00:d6:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  549.728000] ata1.00: configured for UDMA/100
[  549.728000] ata1: EH complete
[  554.120000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  554.120000] ata1.00: (BMDMA stat 0x5)
[  554.120000] ata1.00: cmd c8/00:07:d6:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 3584 in
[  554.120000]          res 51/40:00:d6:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  554.148000] ata1.00: configured for UDMA/100
[  554.148000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  554.148000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  554.148000] Descriptor sense data with sense descriptors (in hex):
[  554.148000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  554.148000]         00 ee b3 d6 
[  554.148000] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  554.148000] end_request: I/O error, dev sda, sector 15643606
[  554.148000] Buffer I/O error on device sda3, logical block 12361
[  554.148000] Buffer I/O error on device sda3, logical block 12362
[  554.148000] Buffer I/O error on device sda3, logical block 12363
[  554.148000] Buffer I/O error on device sda3, logical block 12364
[  554.148000] Buffer I/O error on device sda3, logical block 12365
[  554.148000] Buffer I/O error on device sda3, logical block 12366
[  554.148000] Buffer I/O error on device sda3, logical block 12367
[  554.148000] ata1: EH complete
[  554.148000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  556.380000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  556.380000] ata1.00: (BMDMA stat 0x5)
[  556.380000] ata1.00: cmd c8/00:08:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  556.380000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  556.408000] ata1.00: configured for UDMA/100
[  556.408000] ata1: EH complete
[  558.632000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  558.632000] ata1.00: (BMDMA stat 0x5)
[  558.632000] ata1.00: cmd c8/00:08:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  558.632000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  558.664000] ata1.00: configured for UDMA/100
[  558.664000] ata1: EH complete
[  560.892000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  560.892000] ata1.00: (BMDMA stat 0x5)
[  560.892000] ata1.00: cmd c8/00:08:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  560.892000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  560.928000] ata1.00: configured for UDMA/100
[  560.928000] ata1: EH complete
[  563.156000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  563.156000] ata1.00: (BMDMA stat 0x5)
[  563.156000] ata1.00: cmd c8/00:08:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  563.156000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  563.200000] ata1.00: configured for UDMA/100
[  563.200000] ata1: EH complete
[  565.428000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  565.428000] ata1.00: (BMDMA stat 0x5)
[  565.428000] ata1.00: cmd c8/00:08:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  565.428000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  565.468000] ata1.00: configured for UDMA/100
[  565.468000] ata1: EH complete
[  567.692000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  567.692000] ata1.00: (BMDMA stat 0x5)
[  567.692000] ata1.00: cmd c8/00:08:d5:b3:ee/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  567.692000]          res 51/40:00:d5:b3:ee/00:00:00:00:00/e0 Emask 0x9 (media error)
[  567.720000] ata1.00: configured for UDMA/100
[  567.720000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  567.720000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  567.720000] Descriptor sense data with sense descriptors (in hex):
[  567.720000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  567.720000]         00 ee b3 d5 
[  567.720000] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  567.720000] end_request: I/O error, dev sda, sector 15643605
[  567.720000] Buffer I/O error on device sda3, logical block 12360
[  567.720000] Buffer I/O error on device sda3, logical block 12361
[  567.720000] Buffer I/O error on device sda3, logical block 12362
[  567.720000] Buffer I/O error on device sda3, logical block 12363
[  567.720000] Buffer I/O error on device sda3, logical block 12364
[  567.720000] ata1: EH complete
[  567.720000] sd 0:0:0:0: [sda] Write Protect is off
[  567.720000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  567.720000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  567.720000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  567.720000] sd 0:0:0:0: [sda] Write Protect is off
[  567.720000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  567.720000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

I didn't know where the specific error started so I copied from where it said bcm43xx not available (which I think is normal).

---

### Post by psusi on 2007-12-14
Whoa there we go, disk is bad.  Did you ever check the smartctl -A again after the disk had time to complete its internal check?  It should indicate that it found errors now.

And yea, I meant fsck ;)

---

### Post by corney91 on 2007-12-14
> **psusi said:**
> Whoa there we go, disk is bad.  Did you ever check the smartctl -A again after the disk had time to complete its internal check?  It should indicate that it found errors now.

I've switched it off since, I'll scan it again...

---

### Post by xeth_delta on 2007-12-14
I guess you might be able to use dd to get raw data from the partition and send it to a file on another hdd. Then you might be able to mount it and try recovering some of your data.

Xeth

---

### Post by psusi on 2007-12-14
> **corney91 said:**
> I've switched it off since, I'll scan it again...

That's fine, the drive remembers the results of the last 5 tests even if you power down.

---

### Post by corney91 on 2007-12-14
> **psusi said:**
> That's fine, the drive remembers the results of the last 5 tests even if you power down.

It's in the LiveCD. It should be finished now, so I'll check now.

> **xeth_delta said:**
> I guess you might be able to use dd to get raw data from the partition and send it to a file on another hdd. Then you might be able to mount it and try recovering some of your data.

Xeth

Could you expand on how to do this?

---

### Post by xeth_delta on 2007-12-14
> **corney91 said:**
> Could you expand on how to do this?

It's been long time since I did something like that, I hope I get it right.
First make sure you have **enough disk space** where you are putting the file, since you will be dumping a whole partition's contents on it.

Say you have a parallel ATA hdd and you want to retrieve data from partition hdax. If memory serves right, the command to dump your partitions contents would look like:

```
dd if=/dev/hda**x** of=image_file bs=512
```

Depending on the size of the partition, it might take a while.

To mount the obtained image, assuming your partition was ext3, I think the command would look like:

```
sudo mount image_file /mnt/mount_dir -t ext3 -o loop
```

Any corrections or completions are welcome. Let us know if it worked.

---

### Post by psusi on 2007-12-14
To clarify, you need another hard disk to boot from and store the image file on to do the above.  Also you will want dd_rescue instead of dd since dd will error out when it fails to read part of the disk.

---

### Post by corney91 on 2007-12-14
Here's the output of smartctl -A
```
sudo smartctl -A /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0002   095   095   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   100   100   020    Pre-fail  Always       -       569
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   073   060   030    Pre-fail  Always       -       24641919
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1144
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   100   100   020    Pre-fail  Always       -       871
187 Unknown_Attribute       0x0032   001   001   000    Old_age   Always       -       1082
189 Unknown_Attribute       0x003a   098   098   000    Old_age   Always       -       2
190 Temperature_Celsius     0x0022   054   039   045    Old_age   Always   In_the_past 773193774
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       658
193 Load_Cycle_Count        0x0032   085   085   000    Old_age   Always       -       30813
194 Temperature_Celsius     0x0022   046   061   000    Old_age   Always       -       46 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   089   049   000    Old_age   Always       -       110812737
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       4
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       4
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0


```

Do I dd_rescue if=/dev/sda3 of='an external hardrive' bs=512?
What does the bs mean? Will I have to change the number?
And will it be a file or do I need the whole harddrive?

---

### Post by philinux on 2007-12-14
Just to recap, what happens (errors) when you try to mount the drive from the live cd.

Reason I'm asking as I had this 2 months ago. Ended up backing up my home to a 4gig usb drive then doing a reinstall. I had trouble getting full access to the drive and ended up using a knoppix live cd.

---

### Post by xeth_delta on 2007-12-14
dd_rescue has a different syntax to dd. You have to install it separately. It is in the repositories.
From dd_rescue --help I can see that the command should look like:
```
dd_rescue [options] infile outfile
```
More information with man dd_rescue, I have only used dd before.

If you decide to try dd or dd_rescue, you will most likely have to dump the partition data in question to a file.

---

### Post by psusi on 2007-12-14
Oops, I mean -a to show all info, -A is just the attributes, but it shows there that you have 4 bad sectors.  Check the scan log in smartctl -a, iirc, it will show which sector was bad and we can try to re-write it to correct the problem.

---

### Post by corney91 on 2007-12-14
> **psusi said:**
> Oops, I mean -a to show all info, -A is just the attributes, but it shows there that you have 4 bad sectors.  Check the scan log in smartctl -a, iirc, it will show which sector was bad and we can try to re-write it to correct the problem.

```
sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.2 series
Device Model:     ST9120821AS
Serial Number:    5PL4MXLK
Firmware Version: 7.24
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Dec 14 21:10:49 2007 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121) The previous self-test completed having
                                        the read element of the test failed.
Total time to complete Offline 
data collection:                 ( 426) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  68) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0002   095   095   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   100   100   020    Pre-fail  Always       -       569
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   073   060   030    Pre-fail  Always       -       24641994
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1145
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   100   100   020    Pre-fail  Always       -       871
187 Unknown_Attribute       0x0032   001   001   000    Old_age   Always       -       1082
189 Unknown_Attribute       0x003a   098   098   000    Old_age   Always       -       2
190 Temperature_Celsius     0x0022   055   039   045    Old_age   Always   In_the_past 773193773
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       658
193 Load_Cycle_Count        0x0032   085   085   000    Old_age   Always       -       30817
194 Temperature_Celsius     0x0022   045   061   000    Old_age   Always       -       45 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   088   049   000    Old_age   Always       -       110814804
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       4
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       4
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 2074 (device log contains only the most recent five errors)
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

Error 2074 occurred at disk power-on lifetime: 1141 hours (47 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d5 b3 ee e0 00      00:09:52.371  READ DMA
  ec 00 00 00 00 00 a0 00      00:09:52.354  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:09:52.339  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:09:52.328  IDENTIFY DEVICE
  c8 00 08 d5 b3 ee e0 00      00:09:50.095  READ DMA

Error 2073 occurred at disk power-on lifetime: 1141 hours (47 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d5 b3 ee e0 00      00:09:52.371  READ DMA
  ec 00 00 00 00 00 a0 00      00:09:52.354  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:09:52.339  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:09:52.328  IDENTIFY DEVICE
  c8 00 08 d5 b3 ee e0 00      00:09:50.095  READ DMA

Error 2072 occurred at disk power-on lifetime: 1141 hours (47 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d5 b3 ee e0 00      00:09:45.542  READ DMA
  ec 00 00 00 00 00 a0 00      00:09:43.304  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:09:43.297  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:09:43.288  IDENTIFY DEVICE
  c8 00 08 d5 b3 ee e0 00      00:09:50.095  READ DMA

Error 2071 occurred at disk power-on lifetime: 1141 hours (47 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d5 b3 ee e0 00      00:09:45.542  READ DMA
  ec 00 00 00 00 00 a0 00      00:09:43.304  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:09:43.297  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:09:43.288  IDENTIFY DEVICE
  c8 00 08 d5 b3 ee e0 00      00:09:43.276  READ DMA

Error 2070 occurred at disk power-on lifetime: 1141 hours (47 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d5 b3 ee e0 00      00:09:45.542  READ DMA
  ec 00 00 00 00 00 a0 00      00:09:43.304  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:09:43.297  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:09:43.288  IDENTIFY DEVICE
  c8 00 08 d5 b3 ee e0 00      00:09:43.276  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      1141         15643605
# 2  Extended offline    Interrupted (host reset)      90%      1141         -
# 3  Extended offline    Completed: read failure       90%      1141         15643605

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by psusi on 2007-12-14
Ok, it looks like the first bad sector is number 15643605.  Let's confirm that and try to overwrite it, which should fix it.  

sudo dd bs=512 if=/dev/sda of=/dev/null count=1 skip=15643605

That should fail.. if it does, then let's overwrite it.  

sudo dd bs=512 if=/dev/zero of=/dev/sda count=1 seek=15643605

Then try to read it again and it should work this time.  Then repeat the smartctl -t long test, and check the log again for the next bad sector found.

---

### Post by corney91 on 2007-12-14
> **psusi said:**
> Ok, it looks like the first bad sector is number 15643605.  Let's confirm that and try to overwrite it, which should fix it.  

sudo dd bs=512 if=/dev/sda of=/dev/null count=1 skip=15643605

That should fail.. if it does, then let's overwrite it.  

sudo dd bs=512 if=/dev/zero of=/dev/sda count=1 seek=15643605

Then try to read it again and it should work this time.  Then repeat the smartctl -t long test, and check the log again for the next bad sector found.

That doesn't quite work, but if I use /dev/sda3 it does. Is this what it is meant to be or something different?

---

### Post by psusi on 2007-12-14
Could you be more specific?  What doesn't work?  It should just be sda, not sda3.  Did you just try to read or write as well?  The read on the sda3 should have worked, so you should have stopped there.

---

### Post by corney91 on 2007-12-14
> **psusi said:**
> Could you be more specific?  What doesn't work?  It should just be sda, not sda3.  Did you just try to read or write as well?  The read on the sda3 should have worked, so you should have stopped there.

Sorry, here's the error:```
ubuntu@ubuntu:~$ sudo dd bs=512 if=/dev/sda of=/dev/null count=1 skip=15643605
dd: reading `/dev/sda': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 16.1147 seconds, 0.0 kB/s
ubuntu@ubuntu:~$ sudo dd bs=512 if=/dev/zero of=/dev/sda count=1 seek=15643605
dd: writing `/dev/sda': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 20.433 seconds, 0.0 kB/s

```

The first one fails as you said, but should the second one fail as well?

---

### Post by psusi on 2007-12-15
The attempt to write should either write correct data to that spot on the disk, or if it really is physically damaged, cause the drive to automatically map that address to another good sector in a reserved pool.  Check the output of smartctl -a again.. it may be that for some reason your drive does not support defect mapping.

---

### Post by corney91 on 2007-12-17
> **psusi said:**
> The attempt to write should either write correct data to that spot on the disk, or if it really is physically damaged, cause the drive to automatically map that address to another good sector in a reserved pool.  Check the output of smartctl -a again.. it may be that for some reason your drive does not support defect mapping.

The way I understand it, the write also failed if sudo dd bs=512 if=/dev/zero of=/dev/sda count=1 seek=15643605 fails (am I understanding this correctly?). What is 'defect mapping' and how would I tell if it's supported? Here's smartctl -a:

```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.2 series
Device Model:     ST9120821AS
Serial Number:    5PL4MXLK
Firmware Version: 7.24
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Dec 17 22:17:34 2007 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121) The previous self-test completed having
                                        the read element of the test failed.
Total time to complete Offline 
data collection:                 ( 426) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  68) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0002   095   095   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   100   100   020    Pre-fail  Always       -       572
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   073   060   030    Pre-fail  Always       -       24650776
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1151
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   100   100   020    Pre-fail  Always       -       886
187 Unknown_Attribute       0x0032   001   001   000    Old_age   Always       -       1202
189 Unknown_Attribute       0x003a   098   098   000    Old_age   Always       -       2
190 Temperature_Celsius     0x0022   050   039   045    Old_age   Always   In_the_past 841875506
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       672
193 Load_Cycle_Count        0x0032   085   085   000    Old_age   Always       -       30844
194 Temperature_Celsius     0x0022   050   061   000    Old_age   Always       -       50 (Lifetime Min/Max 0/15)
195 Hardware_ECC_Recovered  0x001a   089   049   000    Old_age   Always       -       111546964
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       4
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       4
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 2248 (device log contains only the most recent five errors)
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

Error 2248 occurred at disk power-on lifetime: 1151 hours (47 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d0 b3 ee e0 00      04:13:08.593  READ DMA
  ec 00 00 00 00 00 a0 00      04:13:17.571  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      04:13:17.565  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      04:13:17.551  IDENTIFY DEVICE
  c8 00 08 d0 b3 ee e0 00      04:13:17.546  READ DMA

Error 2247 occurred at disk power-on lifetime: 1151 hours (47 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d0 b3 ee e0 00      04:13:08.593  READ DMA
  ec 00 00 00 00 00 a0 00      04:13:08.582  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      04:13:06.353  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      04:13:06.345  IDENTIFY DEVICE
  c8 00 08 d0 b3 ee e0 00      04:13:06.333  READ DMA

Error 2246 occurred at disk power-on lifetime: 1151 hours (47 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d0 b3 ee e0 00      04:13:08.593  READ DMA
  ec 00 00 00 00 00 a0 00      04:13:08.582  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      04:13:06.353  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      04:13:06.345  IDENTIFY DEVICE
  c8 00 08 d0 b3 ee e0 00      04:13:06.333  READ DMA

Error 2245 occurred at disk power-on lifetime: 1151 hours (47 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d0 b3 ee e0 00      04:13:08.593  READ DMA
  ec 00 00 00 00 00 a0 00      04:13:08.582  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      04:13:06.353  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      04:13:06.345  IDENTIFY DEVICE
  c8 00 08 d0 b3 ee e0 00      04:13:06.333  READ DMA

Error 2244 occurred at disk power-on lifetime: 1151 hours (47 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d5 b3 ee e0  Error: UNC at LBA = 0x00eeb3d5 = 15643605

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d0 b3 ee e0 00      04:12:26.672  READ DMA
  ec 00 00 00 00 00 a0 00      04:12:26.656  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      04:13:06.353  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      04:13:06.345  IDENTIFY DEVICE
  c8 00 08 d0 b3 ee e0 00      04:13:06.333  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      1150         15643605
# 2  Extended offline    Completed: read failure       90%      1141         15643605
# 3  Extended offline    Interrupted (host reset)      90%      1141         -
# 4  Extended offline    Completed: read failure       90%      1141         15643605

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by psusi on 2007-12-17
Normally the disk will have a pool of reserved sectors set aside for when it develops bad sectors.  When the disk can not write to a sector because it is physically damaged, it picks a sector from the spare pool and uses that sector instead to replace the damaged area.  That process is called defect (re)mapping.

---

### Post by corney91 on 2007-12-17
> **psusi said:**
> Normally the disk will have a pool of reserved sectors set aside for when it develops bad sectors.  When the disk can not write to a sector because it is physically damaged, it picks a sector from the spare pool and uses that sector instead to replace the damaged area.  That process is called defect (re)mapping.

OK. Is it possible to tell if it's supported by the harddrive from the smartctl -a?
I tried 'sudo smartctl -a /dev/sda | grep defect' and a few other words instead of defect but couldn't find anything.

Also, if bs stands for blocksize, should it be 4096 in the dd command?
```
tune2fs -l /dev/sda3 | grep Block
Block count:              27224150
Block size:               4096
Blocks per group:         32768
```

---

### Post by psusi on 2007-12-18
> **corney91 said:**
> OK. Is it possible to tell if it's supported by the harddrive from the smartctl -a?
I tried 'sudo smartctl -a /dev/sda | grep defect' and a few other words instead of defect but couldn't find anything.

Also, if bs stands for blocksize, should it be 4096 in the dd command?
```
tune2fs -l /dev/sda3 | grep Block
Block count:              27224150
Block size:               4096
Blocks per group:         32768
```

No... the filesystem allocates 4k at a time, but the disk stores 512 byte sectors.

If you have another disk that is at least as large as this one, you might be able to use dd_rescue to copy all of the readable parts to that disk, then run a fsck on it there to fix the filesystem.  That might work and recover some or most of your data.

Actually, I have just been playing around with something and I may have come up with a new way to try to recover using device mapper snapshots.  This is the first time I have tried this, but I think it should work.  First, get a list of each bad sector on the disk by running sudo badblocks -n /dev/sda.  Then try the following:

```
sudo -s
dd if=/dev/zero bs=1MiB count=50 /tmp/snapshot
losetup /dev/loop0 /tmp/snapshot
modprobe dm-snapshot
echo 0 $( blockdev --getsize /dev/sda ) snapshot-origin /dev/sda | dmsetup create origin
echo 0 $( blockdev --getsize /dev/sda ) snapshot /dev/mapper/origin /dev/loop0 N 8 | dmsetup create snapshot
```

At this point you should have a new device named /dev/mapper/snapshot such that when you read from it, you will get the contents of sda, but when you write to it, the writes will be stored in a temporary file in ram.  This way you can use dd to write zeros to each of the bad sectors, then you can try to fsck the snapshot and fsck will read zeroes instead of getting errors when trying to read the bad sectors.  At that point fsck may or may not be able to repair the filesystem, and any writes it makes will be kept in ram, so it won't muck up the disk any further.  If it works, you should be able to mount /dev/mapper/snapshot and get your data.

---

### Post by corney91 on 2007-12-18
> **psusi said:**
> No... the filesystem allocates 4k at a time, but the disk stores 512 byte sectors.

If you have another disk that is at least as large as this one, you might be able to use dd_rescue to copy all of the readable parts to that disk, then run a fsck on it there to fix the filesystem.  That might work and recover some or most of your data.

Actually, I have just been playing around with something and I may have come up with a new way to try to recover using device mapper snapshots.  This is the first time I have tried this, but I think it should work.  First, get a list of each bad sector on the disk by running sudo badblocks -n /dev/sda.  Then try the following:

```
sudo -s
dd if=/dev/zero bs=1MiB count=50 /tmp/snapshot
losetup /dev/loop0 /tmp/snapshot
modprobe dm-snapshot
echo 0 $( blockdev --getsize /dev/sda ) snapshot-origin /dev/sda | dmsetup create origin
echo 0 $( blockdev --getsize /dev/sda ) snapshot /dev/mapper/origin /dev/loop0 N 8 | dmsetup create snapshot
```

At this point you should have a new device named /dev/mapper/snapshot such that when you read from it, you will get the contents of sda, but when you write to it, the writes will be stored in a temporary file in ram.  This way you can use dd to write zeros to each of the bad sectors, then you can try to fsck the snapshot and fsck will read zeroes instead of getting errors when trying to read the bad sectors.  At that point fsck may or may not be able to repair the filesystem, and any writes it makes will be kept in ram, so it won't muck up the disk any further.  If it works, you should be able to mount /dev/mapper/snapshot and get your data.

Will this need extra diskspace, aside from /dev/sda?

---

### Post by psusi on 2007-12-18
> **corney91 said:**
> Will this need extra diskspace, aside from /dev/sda?

No, as I said, it will store any modified data in ram instead of modifying the disk.  If fsck is able to fix the filesystem, you should be able to copy all of the data off to some other medium.

---

### Post by psusi on 2007-12-18
Wait... before you do any of that, try sudo fsck -c /dev/sda3.

---

### Post by corney91 on 2007-12-19
> **psusi said:**
> Wait... before you do any of that, try sudo fsck -c /dev/sda3.

Still same error...
```
ubuntu@ubuntu:~$ sudo fsck -c /dev/sda3
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda3: Attempt to read block from filesystem resulted in short read while reading block 1545

/dev/sda3: Attempt to read block from filesystem resulted in short read reading journal superblock

fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sda3
```

Should I continue with the snapshots thing anyway?

---

### Post by psusi on 2007-12-19
Oh crap.. the bad sector would be in the journal wouldn't it?  Yea, I suppose the snapshot thing is worth a try... fsck can't cope with bad sectors in the journal.

---

### Post by philinux on 2007-12-19
I read somewhere that if you delete the journal the file system will revert to ext2. Not sure how to do this - would it help?

---

### Post by psusi on 2007-12-19
Yes, I was thinking of that.. and you do it with tune2fs, but it may cause more damage than the other method depending on the contents of the journal.

---

### Post by corney91 on 2007-12-20
```
ubuntu@ubuntu:~$ sudo badblocks -n /dev/sda
/dev/sda is apparently in use by the system; it's not safe to run badblocks!
```

I get this error everytime I run badblocks. It's unmounted and I've tried running it straight after bootup, but both give the error message. Any ideas how to stop the 'use by the system'?

---

### Post by psusi on 2007-12-20
The livecd is probably using your swap partition.  sudo swapoff -a.  Now that I think about it though, the tune2fs idea may be a better solution.  Disabling the journal may allow fsck -c to correctly repair the damage to the filesystem, then you can turn the journal back on later, and as long as those 4 bad sectors are correctly flagged as bad so they are not used, you should be able to continue to use the disk fine for some time, but keep an eye out for more bad sectors by running the smartctl long test every once in a while.

---

### Post by corney91 on 2007-12-20
> **psusi said:**
> The livecd is probably using your swap partition.  sudo swapoff -a.  Now that I think about it though, the tune2fs idea may be a better solution.  Disabling the journal may allow fsck -c to correctly repair the damage to the filesystem, then you can turn the journal back on later, and as long as those 4 bad sectors are correctly flagged as bad so they are not used, you should be able to continue to use the disk fine for some time, but keep an eye out for more bad sectors by running the smartctl long test every once in a while.

OK, swap's off and badblocks is running. Should I carry on with the snapshot idea or just go for tune2fs? If tune2fs, how could I go about it?

---

### Post by corney91 on 2008-01-05
OK. I've procrastinated enough:)
What options should I give tune2fs to disable the journal?


EDIT:Found [this.]("http://www.linuxquestions.org/questions/linux-general-1/remove-journal-from-ext3-130969/") Would this work?```
tune2fs -O ^has_journal /dev/sda
```

---

### Post by corney91 on 2008-01-15
I think I got rid of the journal, but fsck still doesn't work and tbh it's gone on long enough. So tomorrow I'm reinstalling on his laptop. His coursework was backed up, but pictures will be lost:(
...unless anyone has any other ideas? :crosses fingers:

---

