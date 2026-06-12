---
title: "hard drive auto reformat?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by killaray on 2008-01-22
well i was transfering some files to one of my HD and then i heard a click and my PC froze... i restarted and once rebooted it seems that the drive was reformated.. is that possible? ive never seen anything like this and wanted to know if theres anyway to recover my partition?

---

### Post by stump138 on 2008-01-22
Sounds like your hard drive might have failed.  If you can boot up, see if your hard drive is showing when you do a:

```
sudo fdisk -l
```

if not, use a livecd and see if you can get to your hard drive from that direction

---

### Post by killaray on 2008-01-22
```
Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00c3f475

Disk /dev/hdb doesn't contain a valid partition table

```

---

### Post by mikeyphi on 2008-01-22
Doesn't look good - but before you do anything drastic....if you can - download testdisk (available through Synaptic)...it has an extensive test and recovery system...might help to recover your disk .. looks as though the data got corrupted...but it's unlikely that it formatted itself..more likely that it was searching for where to go!!!

---

### Post by az on 2008-01-22
Stop using the drive.  Your data is still there.  Make an image of thedisk  using gnu-ddrescue.

You will need a disk of equal or greater size to do this.  That's the best way to recover data from the disk.


[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

### Post by killaray on 2008-01-22
> **mikeyphi said:**
> Doesn't look good - but before you do anything drastic....if you can - download testdisk (available through Synaptic)...it has an extensive test and recovery system...might help to recover your disk .. looks as though the data got corrupted...but it's unlikely that it formatted itself..more likely that it was searching for where to go!!!

ive run the program and im here

```
TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/hdb - 203 GB / 189 GiB - CHS 24792 255 63
     Partition               Start        End    Size in sectors













Structure: Ok.


Keys A: add partition, L: load backup, Enter: to continue


```

ive done L and Enter and none do anything.. any ideas?

---

### Post by mikeyphi on 2008-01-22
Unfortunately looks as though you've lost the partition info.....best to go with the info in post #5

---

### Post by killaray on 2008-01-22
> **az said:**
> Stop using the drive.  Your data is still there.  Make an image of thedisk  using gnu-ddrescue.

You will need a disk of equal or greater size to do this.  That's the best way to recover data from the disk.


[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

so after i do that... i just mount the image of the drive, reformat the actual drive and copy the files over?

---

### Post by az on 2008-01-23
Did testdisk scan for a lost partition?  You didn't really mention what you did.


> **killaray said:**
> so after i do that... i just mount the image of the drive, reformat the actual drive and copy the files over?


No, if testdisk can't find the partition, I don't think the filesystem would be intact.  Your best bet is to data-carve the files you need to recover out.

---

### Post by killaray on 2008-01-23
no i dont believe testdisk founr the partition... how exactly do i data-carve?

---

### Post by Sef on 2008-01-23
Read [Damaged Hard Disk]("http://www.cgsecurity.org/wiki/Damaged_Hard_Disk") and [Data Recovery Examples]("http://www.cgsecurity.org/wiki/Damaged_Hard_Disk").

---

### Post by mikeyphi on 2008-01-23
> **killaray said:**
> no i dont believe testdisk founr the partition... how exactly do i data-carve?

Use the guide posted by az
look especially at the section: Data Recovery from damaged filesystem or drive

---

### Post by killaray on 2008-01-24
ok im gonna try to do this, but before i proceed i wanna make sure that me copyin over the hd to another will not reformat the second drive into an exact clone of the damaged one? and will the damaged drive work anymore? like is this a 1 time crash or is the drive dead?

---

### Post by mikeyphi on 2008-01-24
> **killaray said:**
> ok im gonna try to do this, but before i proceed i wanna make sure that me copyin over the hd to another will not reformat the second drive into an exact clone of the damaged one? and will the damaged drive work anymore? like is this a 1 time crash or is the drive dead?

All you should be doing is copying data off the drive that has lost its partition info.....it doesn't sound as though the disk is terminal - yet!! 
So the new disk will have old data but not the partition error (which is just a few bits of data that's been lost or corrupted) 

Get the data and then try repartitioning the old disk but probably wise not to rely on it till you're happy it's not going to crash again!!

---

### Post by killaray on 2008-01-24
ok.. now.. i did it, now both my drives r unallocated i did testdisk on my SATA drive and the partition is there with both everything it copied from the malfunctionin drive.. now in testdisk wut do i select to make it fix the drive? do i write partition structure to disk?

---

### Post by mikeyphi on 2008-01-24
> **killaray said:**
> ok.. now.. i did it, now both my drives r unallocated i did testdisk on my SATA drive and the partition is there with both everything it copied from the malfunctionin drive.. now in testdisk wut do i select to make it fix the drive? do i write partition structure to disk?

Yes - partition the drive but remember it's probably best to give it some hard use before using it for important data!!

---

### Post by killaray on 2008-01-24
i did it, it told me to restart and then i got some fsck error.. tellin me to run it manually... so i booted up and ran fsck on my /dev/sda1 which is my SATA drive and now its tellin me this
```
Group descriptors look bad... trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

can this be fixed or reversed so i could atleast have my SATA drive back to normal?

also get this when tryin to mount
```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

superblock info incase that helps
```
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

     Partition                  Start        End    Size in sectors

  Linux                    0   1  1 60800 254 61  976768000
superblock 0, blocksize=4096
  Linux                    0   1  1 60800 254 61  976768000
superblock 71663616, blocksize=4096
superblock 78675968, blocksize=4096
superblock 102400000, blocksize=4096

```

lil more info, from smart scan this time

SATA first

```
=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

killaray@Killa-PC:~$ sudo --all /dev/hdb
sudo: please use single character options
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
killaray@Killa-PC:~$ sudo  smartctl --all /dev/hdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax 10 family (ATA/133 and SATA/150)
Device Model:     Maxtor 6B200P0
Serial Number:    B408HZ9H
Firmware Version: BAH41B10
User Capacity:    203,928,109,056 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Thu Jan 24 22:24:13 2008 EST
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
data collection:                 (1622) seconds.
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
recommended polling time:        (  82) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   209   206   063    Pre-fail  Always       -       11299
  4 Start_Stop_Count        0x0032   253   253   000    Old_age   Always       -       262
  5 Reallocated_Sector_Ct   0x0033   253   253   063    Pre-fail  Always       -       0
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   252   244   187    Pre-fail  Always       -       35472
  9 Power_On_Minutes        0x0032   186   186   000    Old_age   Always       -       281h+34m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   253   253   000    Old_age   Always       -       276
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   232   253   000    Old_age   Always       -       43
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       26851
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   253   253   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0008   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       0
202 TA_Increase_Count       0x000a   253   251   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       0
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   241   241   000    Old_age   Offline      -       151
210 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
211 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
212 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0

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

```

corrupt drive

```
=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax 10 family (ATA/133 and SATA/150)
Device Model:     Maxtor 6B200P0
Serial Number:    B408HZ9H
Firmware Version: BAH41B10
User Capacity:    203,928,109,056 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Thu Jan 24 22:27:34 2008 EST
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
data collection:                 (1622) seconds.
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
recommended polling time:        (  82) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   209   206   063    Pre-fail  Always       -       11299
  4 Start_Stop_Count        0x0032   253   253   000    Old_age   Always       -       262
  5 Reallocated_Sector_Ct   0x0033   253   253   063    Pre-fail  Always       -       0
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   252   244   187    Pre-fail  Always       -       35500
  9 Power_On_Minutes        0x0032   186   186   000    Old_age   Always       -       281h+37m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   253   253   000    Old_age   Always       -       276
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   232   253   000    Old_age   Always       -       43
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       26851
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   253   253   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0008   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       0
202 TA_Increase_Count       0x000a   253   251   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       0
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   241   241   000    Old_age   Offline      -       151
210 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
211 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
212 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0

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
```

---

### Post by killaray on 2008-01-25
any ideas... i really need to save the info on at least my SATA drive

---

### Post by killaray on 2008-01-25
noone?

---

### Post by killaray on 2008-01-27
well thanx alot guys.. i guess ill reformat and start everything fresh since u guys abandoned me

---

### Post by mikeyphi on 2008-01-28
What's the situation now?

---

### Post by killaray on 2008-01-28
idk.. im pretty sure ive lost everything though.. test drive sees no partition info on any of the drives... let me know wut info u need to see and ill get it up for u

---

### Post by mikeyphi on 2008-01-29
> **killaray said:**
> idk.. im pretty sure ive lost everything though.. test drive sees no partition info on any of the drives... let me know wut info u need to see and ill get it up for u

No partition is correct - that was the original problem. The suggestion was to extract your data from the copy of your 'broken' drive....you have to use the suggested guide (by az) to extract the data and then rewrite to a fresh partition. Remember that you just copied the old disk to the new disk - errors included!!

---

### Post by killaray on 2008-01-29
yea i copied everything over and it screwed up my other drive... thats where we were at

this is my SATA drive that i copied the info to

```
=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

killaray@Killa-PC:~$ sudo --all /dev/hdb
sudo: please use single character options
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
killaray@Killa-PC:~$ sudo  smartctl --all /dev/hdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax 10 family (ATA/133 and SATA/150)
Device Model:     Maxtor 6B200P0
Serial Number:    B408HZ9H
Firmware Version: BAH41B10
User Capacity:    203,928,109,056 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Thu Jan 24 22:24:13 2008 EST
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
data collection:                 (1622) seconds.
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
recommended polling time:        (  82) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   209   206   063    Pre-fail  Always       -       11299
  4 Start_Stop_Count        0x0032   253   253   000    Old_age   Always       -       262
  5 Reallocated_Sector_Ct   0x0033   253   253   063    Pre-fail  Always       -       0
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   252   244   187    Pre-fail  Always       -       35472
  9 Power_On_Minutes        0x0032   186   186   000    Old_age   Always       -       281h+34m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   253   253   000    Old_age   Always       -       276
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   232   253   000    Old_age   Always       -       43
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       26851
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   253   253   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0008   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       0
202 TA_Increase_Count       0x000a   253   251   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       0
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   241   241   000    Old_age   Offline      -       151
210 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
211 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
212 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0

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
```

also idk if this matters but everytime i restart now it says fsck failed with error 8? wut does that all mean?

---

### Post by mikeyphi on 2008-01-29
As I read the suggestions - it was for you to copy all onto a new disk (in case the old had/was about to fail. That seems to be where you are now.....
The next part of the process was to extract the data using ddrescue.

---

### Post by killaray on 2008-01-29
all the guide says is to do this

```
# download ddrescue
wget http://download.savannah.gnu.org/releases/ddrescue/ddrescue-1.3.tar.bz2
# extract the source code
tar xjf ddrescue-1.3.tar.bz2
# compile ddrescue
cd ddrescue-1.3
./configure && make
# first, grab most of the error-free areas in a hurry:
./ddrescue -n /dev/old_disk /dev/new_disk rescued.log
# then try to recover as much of the dicy areas as possible:
ddrescue -r 1 /dev/old_disk /dev/new_disk rescued.log
```

ive done that except for this part

```
# then try to recover as much of the dicy areas as possible:
ddrescue -r 1 /dev/old_disk /dev/new_disk rescued.log
```

my SATA drive which is where i backed up the corrupt drive cannot mount anymore.. this process seems to have ruined that drive too thats where the issue is and wut i tried explaining before

---

### Post by killaray on 2008-01-31
any ideas on wut i can do?

---

### Post by killaray on 2008-02-02
anyone have any suggestions?

---

### Post by killaray on 2008-02-04
abandoned again...

---

### Post by killaray on 2008-02-05
ok i really need help from someone.. this drive wont even reformat

i try this
```
killaray@Killa-PC:~$ sudo mkfs -t ext3 /dev/hdb
mke2fs 1.40.2 (12-Jul-2007)
/dev/hdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
24903680 inodes, 49787136 blocks
2489356 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1520 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 24 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```

this i do
```
killaray@Killa-PC:~$ sudo fsck -f -y /dev/hdb
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```
and i get that nice lil superblock error.. how can i rectify this?

---

