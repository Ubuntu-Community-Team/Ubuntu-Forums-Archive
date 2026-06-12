---
title: "is my hard drive dying?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2008-01-24
i'm running gutsy headless.  it's been crashing lately.  i'm not seeing any errors in the syslog before i do a hard reboot, but i'm seeing this in the syslog during bootup

```

Jan 24 19:32:47 white kernel: [  100.602698] Adding 1895628k swap on /dev/hda5.  Priority:-1 extents:1 across:1895628k
Jan 24 19:32:47 white kernel: [  101.807671] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan 24 19:32:47 white kernel: [  101.807684] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan 24 19:32:47 white kernel: [  101.807691] ide: failed opcode was: unknown
Jan 24 19:32:47 white kernel: [  102.415207] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan 24 19:32:47 white kernel: [  102.415219] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan 24 19:32:47 white kernel: [  102.415226] ide: failed opcode was: unknown
Jan 24 19:32:47 white kernel: [  103.061527] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan 24 19:32:47 white kernel: [  103.061540] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan 24 19:32:47 white kernel: [  103.061547] ide: failed opcode was: unknown
Jan 24 19:32:47 white kernel: [  103.658071] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan 24 19:32:47 white kernel: [  103.658084] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan 24 19:32:47 white kernel: [  103.658091] ide: failed opcode was: unknown
Jan 24 19:32:47 white kernel: [  103.658345] hdd: DMA disabled
Jan 24 19:32:47 white kernel: [  103.943019] ide1: reset: success
Jan 24 19:32:47 white kernel: [  104.519852] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan 24 19:32:47 white kernel: [  104.519866] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan 24 19:32:47 white kernel: [  104.519873] ide: failed opcode was: unknown
Jan 24 19:32:47 white kernel: [  105.115626] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan 24 19:32:47 white kernel: [  105.115639] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan 24 19:32:47 white kernel: [  105.115646] ide: failed opcode was: unknown
Jan 24 19:32:47 white kernel: [  105.739086] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan 24 19:32:47 white kernel: [  105.739100] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan 24 19:32:47 white kernel: [  105.739107] ide: failed opcode was: unknown
Jan 24 19:32:47 white kernel: [  106.329411] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan 24 19:32:47 white kernel: [  106.329423] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan 24 19:32:47 white kernel: [  106.329430] ide: failed opcode was: unknown

```
I figure that can't be good...

hdparm -vi /dev/hdc gives me the following:

```

/dev/hdc:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 19457/255/63, sectors = 312581808, start = 0

 Model=ST3160023A, FwRev=3.06, SerialNo=3JS0JP6V
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 *udma3 udma4 udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

```

Any advice is appreciated.  I'm having big problems the last two days.  I was up for two weeks with no issues prior to rebooting.  
Is there anything analogous to defragging I can/should do?  (I realize it's generally not necessary in *nix)

---

### Post by SeanTater on 2008-01-24
BadCRC is a BadSign. :) If you can, backup everything there. Reformatting that drive might help, but you seem to have a lot of corrupt files/sectors.

Regardless of if it's in error, it may be a precursor to total failure (if it's not already happened).

You will also want to look into SMART (it will test your hard drive's health). It's in the package smartmontools.

To test your hard drive use:```
 smartctl --smart=on /dev/hdc
 smartctl --all /dev/hdc 
```


On the other hand -- If it's a CD drive -- it's probably the CD. You'll need to get the data off of it, but the drive is probably fine.

---

### Post by randomjohn on 2008-01-24
thanks for the tip... what does this mean, though?

```

 smartctl --smart=on /dev/hdc
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

~$ sudo smartctl --all /dev/hdc
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST3160023A
Serial Number:    3JS0JP6V
Firmware Version: 3.06
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Thu Jan 24 21:50:36 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 ( 430) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off supp                       ort.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 111) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_                       FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   059   052   006    Pre-fail  Always       -                              8716816
  3 Spin_Up_Time            0x0003   097   096   000    Pre-fail  Always       -                              0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -                              47
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -                              0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -                              254829436
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -                              22725
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -                              0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -                              195
194 Temperature_Celsius     0x0022   052   063   000    Old_age   Always       -                              52
195 Hardware_ECC_Recovered  0x001a   059   052   000    Old_age   Always       -                              8716816
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -                              0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -                              0
199 UDMA_CRC_Error_Count    0x003e   200   181   000    Old_age   Always       -                              2093
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -                              0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -                              0

SMART Error Log Version: 1
ATA Error Count: 11985 (device log contains only the most recent five errors)
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

Error 11985 occurred at disk power-on lifetime: 22723 hours (946 days + 19 hours                       )
  When the command that caused the error occurred, the device was active or idle                       .

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 46 de 23 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x0023de46 = 235066                       2

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 1e 29 de 23 e0 00      00:01:47.368  READ DMA EXT
  25 00 1e 29 de 23 e0 00      00:01:46.761  READ DMA EXT
  10 00 3f 00 00 00 e0 00      00:01:46.174  RECALIBRATE [OBS-4]
  25 00 1e 29 de 23 e0 00      00:01:46.055  READ DMA EXT
  25 00 1e 29 de 23 e0 00      00:01:45.884  READ DMA EXT

Error 11984 occurred at disk power-on lifetime: 22723 hours (946 days + 19 hours                       )
  When the command that caused the error occurred, the device was active or idle                       .

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 46 de 23 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x0023de46 = 235066                       2

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 1e 29 de 23 e0 00      00:01:47.368  READ DMA EXT
  10 00 3f 00 00 00 e0 00      00:01:46.761  RECALIBRATE [OBS-4]
  25 00 1e 29 de 23 e0 00      00:01:46.174  READ DMA EXT
  25 00 1e 29 de 23 e0 00      00:01:46.055  READ DMA EXT
  00 00 44 00 00 00 00 06      00:01:45.884  NOP [Abort queued commands]

Error 11983 occurred at disk power-on lifetime: 22723 hours (946 days + 19 hours                       )
  When the command that caused the error occurred, the device was active or idle                       .

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 46 de 23 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x0023de46 = 235066                       2

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 1e 29 de 23 e0 00      00:01:43.365  READ DMA EXT
  25 00 1e 29 de 23 e0 00      00:01:46.761  READ DMA EXT
  00 00 44 00 00 00 00 06      00:01:46.174  NOP [Abort queued commands]
  ef 03 44 46 de 23 e0 02      00:01:46.055  SET FEATURES [Set transfer mode]
  25 00 1e 29 de 23 e0 00      00:01:45.884  READ DMA EXT

Error 11982 occurred at disk power-on lifetime: 22723 hours (946 days + 19 hours                       )
  When the command that caused the error occurred, the device was active or idle                       .

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 46 de 23 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x0023de46 = 235066                       2

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 1e 29 de 23 e0 00      00:01:43.365  READ DMA EXT
  00 00 44 00 00 00 00 06      00:01:43.358  NOP [Abort queued commands]
  ef 03 44 46 de 23 e0 02      00:01:46.174  SET FEATURES [Set transfer mode]
  25 00 1e 29 de 23 e0 00      00:01:46.055  READ DMA EXT
  25 00 1e 29 de 23 e0 00      00:01:45.884  READ DMA EXT

Error 11981 occurred at disk power-on lifetime: 22723 hours (946 days + 19 hours                       )
  When the command that caused the error occurred, the device was active or idle                       .

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 46 de 23 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x0023de46 = 235066                       2

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 1e 29 de 23 e0 00      00:01:43.365  READ DMA EXT
  25 00 1e 29 de 23 e0 00      00:01:43.358  READ DMA EXT
  10 00 3f 00 00 00 e0 00      00:01:43.357  RECALIBRATE [OBS-4]
  25 00 1e 29 de 23 e0 00      00:01:43.351  READ DMA EXT
  25 00 1e 29 de 23 e0 00      00:01:43.350  READ DMA EXT

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

```...and more importantly, is there anything I can do other than backup and yank the drive?

---

