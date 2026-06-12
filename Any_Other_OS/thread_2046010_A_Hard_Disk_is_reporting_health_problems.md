---
title: "A Hard Disk is reporting health problems"
date: 2012-08-22
forum: Any Other OS
---

### Post by tech291083 on 2012-08-22
Hi,

I have Fedora 16 32 bit installed on a 80 GB SATA HDD as the only OS and it is showing the following error. Please help.

**A Hard Disk is reporting health problems.**

```


[root@localhost john]# smartctl -s on -a /dev/sda



smartctl 5.43 2012-06-30 r3573 [i686-linux-3.1.0-7.fc16.i686.PAE] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint P80 SD
Device Model:     SAMSUNG HD080HJ
Serial Number:    xxxxxxxxxxxxxxxxxx
Firmware Version: ZH100-41
User Capacity:    80,026,361,856 bytes [80.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Wed Aug 22 18:39:46 2012 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x02)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (  73)    The previous self-test completed having
                    a test element that failed and the test
                    element that failed is not known.
Total time to complete Offline 
data collection:         ( 1872) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  31) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   099   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   100   100   025    Pre-fail  Always       -       3904
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1949
  5 Reallocated_Sector_Ct   0x0033   001   001   010    Pre-fail  Always   FAILING_NOW 1627
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       964
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1323
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       12059317
190 Airflow_Temperature_Cel 0x0022   091   073   000    Old_age   Always       -       49
194 Temperature_Celsius     0x0022   091   073   000    Old_age   Always       -       49
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1922190
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       1627
197 Current_Pending_Sector  0x0012   253   097   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   095   000    Old_age   Always       -       0
202 Data_Address_Mark_Errs  0x0032   253   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 653 (device log contains only the most recent five errors)
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

Error 653 occurred at disk power-on lifetime: 936 hours (39 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 c0 b9 12 e8  Error: UNC at LBA = 0x0812b9c0 = 135444928

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 c0 b9 12 e8 00      00:00:39.250  READ DMA
  ec 00 00 00 00 00 a0 00      00:00:37.250  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:00:37.250  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:00:37.188  IDENTIFY DEVICE

Error 652 occurred at disk power-on lifetime: 936 hours (39 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 c0 b9 12 e8  Error: UNC at LBA = 0x0812b9c0 = 135444928

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 c0 b9 12 e8 00      00:00:37.125  READ DMA
  ec 00 00 00 00 00 a0 00      00:00:35.375  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:00:35.375  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:00:35.250  IDENTIFY DEVICE

Error 651 occurred at disk power-on lifetime: 936 hours (39 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 c0 b9 12 e8  Error: UNC at LBA = 0x0812b9c0 = 135444928

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 c0 b9 12 e8 00      00:00:35.188  READ DMA
  ec 00 00 00 00 00 a0 00      00:00:33.438  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:00:33.375  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:00:33.313  IDENTIFY DEVICE

Error 650 occurred at disk power-on lifetime: 936 hours (39 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 c0 b9 12 e8  Error: UNC at LBA = 0x0812b9c0 = 135444928

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 c0 b9 12 e8 00      00:00:33.250  READ DMA
  c8 00 80 40 b9 12 e8 00      00:00:31.500  READ DMA
  c8 00 08 20 b9 13 e8 00      00:00:31.500  READ DMA
  c8 00 08 00 b9 13 e8 00      00:00:31.500  READ DMA
  c8 00 40 00 b9 12 e8 00      00:00:31.500  READ DMA

Error 649 occurred at disk power-on lifetime: 936 hours (39 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 18 ba 12 e8  Error: UNC 240 sectors at LBA = 0x0812ba18 = 135445016

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 f0 18 ba 12 e8 00      00:02:44.625  READ DMA
  c8 00 08 10 ba 12 e8 00      00:02:42.750  READ DMA
  c8 00 08 08 ba 12 e8 00      00:02:42.750  READ DMA
  c8 00 08 40 ba 13 e8 00      00:02:42.750  READ DMA
  c8 00 f8 10 bc 12 e8 00      00:02:42.750  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: unknown failure    90%       954         0
# 2  Short offline       Completed: unknown failure    90%       952         0
# 3  Short offline       Completed: unknown failure    90%       952         0

Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
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

### Post by TheFu on 2012-08-22
SMART isn't usually very useful, but when it says to **SAVE ALL DATA**, you should listen.
"Pre-fail" means little most of the time.

**Drive failure expected in less than 24 hours. SAVE ALL DATA.**
I'd definitely make certain that the incremental backups worked well and I'd be prepared to swap disks shortly. It there is a "production" system, I'd schedule some downtime for tonight to swap the HDD, hopefully before it fails.  At home, I might use the HDD for backups, but never again would it be trusted for primary data without additional testing using available HDD tools from the vendor and a commercial tool.

---

### Post by tech291083 on 2012-08-22
> **TheFu said:**
> SMART isn't usually very useful, but when it says to SAVE ALL DATA, you should listen.
"Pre-fail" means little most of the time.


Ok. I have copied all my data to another drive already using the Fedora 16 Live CD. So I am not much worried about losing it. All I want to know is how to resolve this issue which has hit me for the first time ever.

I have been reading on the net on various forums about this particular error and getting contradictory opinions, which have really confused me a lot. some people say that they have had similar warnings it the past for a number of different make of HDDs and nothing bad has happened in 24 hours ie their hard disk have not crashed in 24 hours as indicated in the error message. Their drives are running well without any problems whatsoever.

Please tell me what to do? I have also read that SMART data is no that correct and one should just disable the warning ie tick the checkbox next to Don't warn if the disk is failing in the SMART Data window in Disk Utility program.

Can you please tell me which free programs I can download which tend to provide more reliable data/tests on my hard drive? I use Fedora and Ubuntu only as of now and no Windows at all.

I need a good solution to this problem so that I can deal with the same more accurately in future.

SMART self-test - Extended 


```


[root@localhost john]#  smartctl --test=long /dev/sda



smartctl 5.43 2012-06-30 r3573 [i686-linux-3.1.0-7.fc16.i686.PAE] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint P80 SD
Device Model:     SAMSUNG HD080HJ
Serial Number:    S08EJ1NL710589
Firmware Version: ZH100-41
User Capacity:    80,026,361,856 bytes [80.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Wed Aug 22 20:32:36 2012 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x02)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (  73)    The previous self-test completed having
                    a test element that failed and the test
                    element that failed is not known.
Total time to complete Offline 
data collection:         ( 1872) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  31) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   099   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   100   100   025    Pre-fail  Always       -       3904
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1949
  5 Reallocated_Sector_Ct   0x0033   001   001   010    Pre-fail  Always   FAILING_NOW 1627
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       966
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1323
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       12059317
190 Airflow_Temperature_Cel 0x0022   091   073   000    Old_age   Always       -       49
194 Temperature_Celsius     0x0022   091   073   000    Old_age   Always       -       49
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1941552
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       1627
197 Current_Pending_Sector  0x0012   253   097   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   095   000    Old_age   Always       -       0
202 Data_Address_Mark_Errs  0x0032   253   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 653 (device log contains only the most recent five errors)
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

Error 653 occurred at disk power-on lifetime: 936 hours (39 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 c0 b9 12 e8  Error: UNC at LBA = 0x0812b9c0 = 135444928

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 c0 b9 12 e8 00      00:00:39.250  READ DMA
  ec 00 00 00 00 00 a0 00      00:00:37.250  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:00:37.250  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:00:37.188  IDENTIFY DEVICE

Error 652 occurred at disk power-on lifetime: 936 hours (39 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 c0 b9 12 e8  Error: UNC at LBA = 0x0812b9c0 = 135444928

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 c0 b9 12 e8 00      00:00:37.125  READ DMA
  ec 00 00 00 00 00 a0 00      00:00:35.375  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:00:35.375  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:00:35.250  IDENTIFY DEVICE

Error 651 occurred at disk power-on lifetime: 936 hours (39 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 c0 b9 12 e8  Error: UNC at LBA = 0x0812b9c0 = 135444928

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 c0 b9 12 e8 00      00:00:35.188  READ DMA
  ec 00 00 00 00 00 a0 00      00:00:33.438  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:00:33.375  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:00:33.313  IDENTIFY DEVICE

Error 650 occurred at disk power-on lifetime: 936 hours (39 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 c0 b9 12 e8  Error: UNC at LBA = 0x0812b9c0 = 135444928

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 c0 b9 12 e8 00      00:00:33.250  READ DMA
  c8 00 80 40 b9 12 e8 00      00:00:31.500  READ DMA
  c8 00 08 20 b9 13 e8 00      00:00:31.500  READ DMA
  c8 00 08 00 b9 13 e8 00      00:00:31.500  READ DMA
  c8 00 40 00 b9 12 e8 00      00:00:31.500  READ DMA

Error 649 occurred at disk power-on lifetime: 936 hours (39 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 18 ba 12 e8  Error: UNC 240 sectors at LBA = 0x0812ba18 = 135445016

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 f0 18 ba 12 e8 00      00:02:44.625  READ DMA
  c8 00 08 10 ba 12 e8 00      00:02:42.750  READ DMA
  c8 00 08 08 ba 12 e8 00      00:02:42.750  READ DMA
  c8 00 08 40 ba 13 e8 00      00:02:42.750  READ DMA
  c8 00 f8 10 bc 12 e8 00      00:02:42.750  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: unknown failure    90%       965         0
# 2  Extended offline    Completed: unknown failure    90%       954         0
# 3  Short offline       Completed: unknown failure    90%       952         0
# 4  Short offline       Completed: unknown failure    90%       952         0

Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
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

### Post by TheFu on 2012-08-22
> **tech291083 said:**
> Please tell me what to do?

This is a judgment call. There is no exact answer. 
I can only say what I would do.

[LIST=1]
[*]backup all the data
[*]swap out the drive ASAP
[*]file for a warranty replacement of the HDD with the vendor
[*]each drive maker has a diagnostic tool for their specific drives - look that up, download it and run it
[*]at work, never trust the drive again - data is too important
[*]at home, relegate the drive to backups only.
[/LIST]
I don't trust any free programs to make a drive *all better.*  Once the number of relocation sectors available is zero, the HDD can't do anything more to automatically recover failing sectors.



Using DD to copy off all data, then DD to copy it back might "refresh" any lazy bits.  It will certainly exercise the drive a bunch and hopefully it will cause a drive to fail sooner than later. Then you'd know it was really dying, right?  OTOH, the lack of available relocation sectors is not good.



Lazy bits are a common cause for the Windows BSOD. I've never had that issue on Linux machines.  Using DD to replicate all the data off and back will certainly refresh the bits.

**Every hard drive is going to fail. The trick is not to care when that happens.**



In the end, it comes down to **how much is the data on those HDDs worth?**  More or less than the price of a new HDD?  For me, a $100 replacement HDD is nothing compared to the data on the drive.

---

### Post by critin on 2012-08-23
With that many errors/bad sectors, I'd assume the Smart Date was correct and the disk is failing.  

You might could run it until it finally quits for good if you have everything off that you care about, but I would get another as soon as possible.

Run test disk and see what it shows.  That takes a long time....
(then mine the gold from it)  lol

---

