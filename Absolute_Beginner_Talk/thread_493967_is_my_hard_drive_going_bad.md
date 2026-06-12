---
title: "is my hard drive going bad?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Dudeman02379 on 2007-07-06
I am having a weird problem on my laptop.  I installed feisty on it yesterday.  It runs fine for a couple of minutes then totally locks up for about a minute then starts running fine again.  I opened the system log veiwer and under the syslog I can see whats happening.  Every few minutes (probably like 4-5 minutes)  it comes up with 

ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata1.00: cmd ca/00:08:ed:42:ef/00:00:00:00:00/e7 tag 0 cdb 0xle data 4096 out
               res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
ata1: soft resetting port
ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
ata1.00: configured for UDMA/33
ata1.00: configured for UDMA/33
ata1: EH complete
SCSI device sda: 156368016 512-Byte hdwr sectors (80060 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

This looks like a hard drive problem to me but I'm an ignorant newb.  Can someone help?

---

### Post by twiceasworn on 2007-07-06
I would agree that it looks like a hard drive issue.  However, it could be any number of things that could be causing the issue.  What are specs of your system?  How old is the drive?  Need a little more information to go on.

EDIT:
Actually I think it is an issue with the software talking to the hard drive.  run hdparm -I /dev/sda in the command line, what is the result?

---

### Post by Dudeman02379 on 2007-07-06
System is only about 2.5 years old.  It's has a pentium m 1.6 ghz processor.  512 mb of memory.  80gb drive.  Let me know what else you need to know.  Thanks.

That command gave a bunch of information.  Is there anything specific that you want to know?  I guess I could type it all in...  I'm not on the internet with that machine right now.

---

### Post by twiceasworn on 2007-07-06
run hdparm -I /dev/sda in the command line, what is the result?

---

### Post by Dudeman02379 on 2007-07-06
/dev/sda:

ATA device, with non-removable media
        Model Number:       SAMSUNG MP0804H                         
        Serial Number:      S042J10Y362739      
        Firmware Revision:  UE100-14
Standards:
        Used: ATA/ATAPI-7 T13 1532D revision 0 
        Supported: 7 6 5 4 
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  156368016
        LBA48  user addressable sectors:  156368016
        device size with M = 1024*1024:       76351 MBytes
        device size with M = 1000*1000:       80060 MBytes (80 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: unknown setting (0x0080)
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
                SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                Advanced Power Management feature set
                SET_MAX security extension
                Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    IDLE_IMMEDIATE with UNLOAD
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
                supported: enhanced erase
        88min for SECURITY ERASE UNIT. 88min for ENHANCED SECURITY ERASE UNIT.
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct

---

### Post by Dudeman02379 on 2007-07-06
Anyone?  any help?  Is there anything else that I can post to help find the problem?

---

### Post by twiceasworn on 2007-07-06
Strange.  When i was looking through google i saw that the Hitatchi drives have issues, but since this is samsung I am at a loss.  Give a little bit to look into it further.

---

### Post by twiceasworn on 2007-07-06
could you open up the terminal and do an "lspci"?  Also, I would run "fsck" to check your hard drive for errors.  I am thinking the hard drive is dying.

---

### Post by Dudeman02379 on 2007-07-06
lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
01:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
01:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
01:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller

fsck warned me that running e2fsck on a mounted filesystem may cause severe damage.  How should I run it?

---

### Post by Dudeman02379 on 2007-07-06
Bummer it looks like you guys are stumped.  I have vista and xp running on other partitions and they are still working fine.  I don't think it is a physical problem with the hard drive.  Anyone have any ideas or anything else I can do to help find the problem?  Thanks for all the help so far.

---

### Post by Dudeman02379 on 2007-07-06
Bump.... Please?  I would really not like to go back to windows but this is unusable in this state.

---

### Post by strider1551 on 2007-07-06
> fsck warned me that running e2fsck on a mounted filesystem may cause severe damage. How should I run it?

Get a live CD and run it from there.  I'm not sure if it's on the Ubuntu CDs, but I'm pretty sure Knoppix has it.

---

### Post by Dudeman02379 on 2007-07-10
Still no luck.  Does anyone have any other ideas?

---

### Post by Dudeman02379 on 2007-07-10
Well I guess no more ubuntu for me... I can't work with it like this so I will be formating the space with ntfs to create more room for my vista install.  As slow as vista is it is faster than ubuntu in this state.:(

---

### Post by ~~Tito~~ on 2007-07-10
No, no. Wait. Just reinstall it. I had problems with stuff and i reinstalled and was fine. Sometimes ubuntu loads wrong on your system.

---

### Post by Dudeman02379 on 2007-07-10
I've reinstalled onece with a live cd and twice with the alternate cd with no luck.

---

### Post by stoanhart on 2007-10-30
You've probably got this:

[https://launchpad.net/bug59695.html](https://launchpad.net/bug59695.html)

I have the same hard drive, and my load/unload cycle count is over 1.7 MILLION! The drive is rated for 300,000... I am expecting mine to die any day now.

With this drive on my Asus Z71V, I am getting 4-5 cycles per minutes. Windows won't do that, which is why the drive probably still works there.

Check your load/unload count with:
```
sudo smartctl -A /dev/sda
```

Obviously, replace /dev/sda with your hard drive (probably the same).

I have tried the "turn off APM" solution:

```

sudo hdparm -B 255 /dev/sda

/dev/sda:
  setting Advanced Power Management level to disabled

```

But when I check the status, I get this:

```

sudo hdparm -I /dev/sda | grep "Advanced power management"
Advanced power management level: unknown setting (0x0080)

```

Hope someone fixes this soon, so that when I replace this drive the next one doesn't get fscked up too... :(

---

### Post by stoanhart on 2007-10-30
HA!

I found my solution!!!

```
smartctl -o on /dev/sda
```

My cycle count has not increased since I did that. I went from exactly 5/min (just benched it 2 minutes ago), to 0/min!

W00t!


Now to see how much longer this drive holds out for...

---

### Post by corax on 2007-11-29
stoanhart !!! YOU ROCK !!!

Thank you !!!

I've been very nervous because my notebook is only 2 years old and my load count is over 670000 and increased with 1 or 2 in about every 5 seconds when the drive was idle and I've started to get bad sectors too (reallocated sector count).

I have a Samsung MP0804H 80 GB notebook HDD. The
```
hdparm -B 255 /dev/XXX
```

method did't work. Neither did with -B 254 or less. 

I have just wrote it down for others who has the same problem.

Thanks stoanhart !!! You've saved my disk's life :)

---

### Post by ubuntu_demon on 2007-11-29
When you are seeing this type of errors you need to make backups and use the tool recommended by your harddrive manufacturer. There's a good chance you need to start shopping for a new harddrive.

---

### Post by stoanhart on 2007-12-02
Glad to help :)

I was pretty excited too when I found that solution.

---

### Post by Trevorius on 2007-12-02
I'm hoping my HD isn't failing already - I just bought this system early October. I started getting a "status bad" warning from SMART during boots, and I got this from the terminal:

trevorius@Megabook:~$ sudo smartctl -d ata -a /dev/sda
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD1600BEVS-22RST0
Serial Number:    WD-WXEZ06722855
Firmware Version: 04.01G04
User Capacity:    160,041,885,696 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Dec  2 22:50:43 2007 AST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 (7200) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  92) minutes.
Conveyance self-test routine
recommended polling time:        (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       15
  3 Spin_Up_Time            0x0003   186   185   021    Pre-fail  Always       -       1675
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       252
  5 Reallocated_Sector_Ct   0x0033   135   135   140    Pre-fail  Always   FAILING_NOW 518
  7 Seek_Error_Rate         0x000f   100   253   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       619
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       248
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       82
193 Load_Cycle_Count        0x0032   196   196   000    Old_age   Always       -       12401
194 Temperature_Celsius     0x0022   117   085   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   089   089   000    Old_age   Always       -       111
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

Can someone tell me what it means? Hopefully it's a software issue...

---

### Post by stoanhart on 2007-12-03
It looks like you have bad sectors. Your load/unload cycle count is not that high, so it doesn't seem to be a due to the "hard drive killer bug".

But yeah, your drive is probably failing. It is probably just be a case of a bad drive, which happens. Exchange it under warranty.

---

### Post by Trevorius on 2007-12-06
> **stoanhart said:**
> It looks like you have bad sectors. Your load/unload cycle count is not that high, so it doesn't seem to be a due to the "hard drive killer bug".

But yeah, your drive is probably failing. It is probably just be a case of a bad drive, which happens. Exchange it under warranty.
Thanks, I think I'll just buy a new one, since I ordered the computer online and i would have to pay $50 each way to ship the comp back.

---

### Post by ubuntu_demon on 2007-12-06
When you are seeing this type of errors you need to make backups and use the diagnostic tool recommended by your harddrive manufacturer. There's a good chance you need to start shopping for a new harddrive.

---

### Post by svguy on 2007-12-14
Is my hard drive going bad?  Thanks

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD series (30-60 GB)
Device Model:     TOSHIBA MK3021GAS
Serial Number:    74R57297T
Firmware Version: GA129D
User Capacity:    30,005,821,440 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Dec 13 23:38:42 2007 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 ( 295) seconds.
Offline data collection
capabilities:                    (0x1b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  33) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       857
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       1651
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       5725
 10 Spin_Retry_Count        0x0033   132   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1641
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       116
193 Load_Cycle_Count        0x0032   090   090   000    Old_age   Always       -       102260
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       37 (Lifetime Min/Max 55/65531)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       122
222 Loaded_Hours            0x0032   091   091   000    Old_age   Always       -       3831
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       394
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      5682         -
# 2  Short offline       Completed without error       00%         2         -

Device does not support Selective Self Tests/Logging

---

### Post by IeU on 2007-12-14
```
[root@minwinpc home]# smartctl -A /dev/sda
smartctl version 5.37 [i386-redhat-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   065   052   006    Pre-fail  Always       -       100802772
  3 Spin_Up_Time            0x0003   096   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       127
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       8
  7 Seek_Error_Rate         0x000f   087   060   030    Pre-fail  Always       -       645858235
  9 Power_On_Hours          0x0032   081   081   000    Old_age   Always       -       17030
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       327
194 Temperature_Celsius     0x0022   046   058   000    Old_age   Always       -       46
195 Hardware_ECC_Recovered  0x001a   065   052   000    Old_age   Always       -       100802772
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

[root@minwinpc home]# 
[root@minwinpc home]# 
[root@minwinpc home]# 
[root@minwinpc home]# smartctl -A /dev/sdb
smartctl version 5.37 [i386-redhat-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   169   167   021    Pre-fail  Always       -       4575
  4 Start_Stop_Count        0x0032   100   100   040    Old_age   Always       -       104
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3221
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       103
194 Temperature_Celsius     0x0022   094   083   000    Old_age   Always       -       53
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0012   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

[root@minwinpc home]# 
[root@minwinpc home]# 
[root@minwinpc home]# 
[root@minwinpc home]# smartctl -A /dev/sdc
smartctl version 5.37 [i386-redhat-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   185   163   021    Pre-fail  Always       -       5716
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       104
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3238
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       102
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       97
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       105
194 Temperature_Celsius     0x0022   104   090   000    Old_age   Always       -       46
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

[root@minwinpc home]# 

```

---

### Post by spydon on 2007-12-14
You can do:

```
badblocks /dev/hda
``` or whatever the name is on your harddrive to check if it has badblocks.

---

### Post by psusi on 2007-12-14
> **svguy said:**
> Is my hard drive going bad?  Thanks


Other than being rather old, it looks fine.  What gave you the idea that it was bad?

---

### Post by svguy on 2007-12-14
> **psusi said:**
> Other than being rather old, it looks fine.  What gave you the idea that it was bad?
[http://ubuntuforums.org/showthread.php?t=631932](http://ubuntuforums.org/showthread.php?t=631932)

I installed XP on my original hard drive and the problems continued. I swapped hard drives and put ubuntu back on and i've rebooted about 6 times now without incident.

---

