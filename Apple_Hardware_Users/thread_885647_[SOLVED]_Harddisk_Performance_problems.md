---
title: "[SOLVED] Harddisk Performance problems"
date: 2008-08-10
forum: Apple Hardware Users
---

### Post by AmberWillow on 2008-08-10
Hi, I'm suffering from performance problems with ubuntu 8.04 clean install on an intel iMac 20".

I used to have a double boot osX / ubuntu, but never used osX anymore. I've messed a bit too much with my ubuntu install, so opted to do a clean install and whiped my osX partition to create 2 new ones. one for /, one for /home in its stead.

Formatting these partitions already took ages. So did installation.
current setup is as follows:

/dev/sda1 fat32 (the old boot partition, i kept as is, 200 mb)
/dev/sda2 ext3 /home 30 gig
/dev/sda5 ext3 / 100 gig
/dev/sda3 linux-swap 1 gig
/dev/sda4 /mnt/oldubuntu 100 gig

sda2 and 5 used to be my old mac partition.

bonnie came up with the following:

> 
Writing with putc()...done
Writing intelligently...done
Rewriting...done
Reading with getc()...done
Reading intelligently...done
start 'em...done...done...done...
Create files in sequential order...done.
Stat files in sequential order...done.
Delete files in sequential order...done.
Create files in random order...done.
Stat files in random order...done.
Delete files in random order...done.
Version 1.03b       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
amber-ubuntu  3000M   423   0   435   0   417   0 20307  36 54421  12 201.4   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
amber-ubuntu,3000M,423,0,435,0,417,0,20307,36,54421,12,201.4,0,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++


which shows that output is the problem, at 500 k/s average, while input looks normal between 2 and 5 mb/sec

"hdparm /dev/sda" is showing the following:
> 
/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 488397168, start = 0


sudo smartctl --all /dev/sda
> 

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar SE (Serial ATA) family
Device Model:     WDC WD2500JS-40TGB0
Serial Number:    WD-WCANY1904855
Firmware Version: 20.06C04
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Aug 10 16:48:56 2008 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (8280) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  97) minutes.
Conveyance self-test routine
recommended polling time: 	 (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   221   183   021    Pre-fail  Always       -       3933
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2336
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   085   085   000    Old_age   Always       -       11179
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0013   100   100   051    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       143
194 Temperature_Celsius     0x0022   104   099   000    Old_age   Always       -       46
195 Hardware_ECC_Recovered  0x000e   155   153   000    Old_age   Always       -       603109
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Aborted by host               90%      8580         -
# 2  Short offline       Aborted by host               90%      7125         -
# 3  Short offline       Aborted by host               90%      6559         -
# 4  Short offline       Aborted by host               90%      6337         -
# 5  Short offline       Aborted by host               90%      5803         -
# 6  Short offline       Aborted by host               90%      5792         -
# 7  Short offline       Aborted by host               90%      5792         -
# 8  Short offline       Aborted by host               90%      5751         -
# 9  Short offline       Aborted by host               90%      5747         -
#10  Short offline       Aborted by host               90%      5734         -
#11  Short offline       Aborted by host               90%      5699         -
#12  Short offline       Aborted by host               90%      5682         -
#13  Short offline       Aborted by host               90%      5662         -
#14  Short offline       Aborted by host               90%      5662         -
#15  Short offline       Aborted by host               90%      5647         -
#16  Short offline       Aborted by host               90%      5646         -
#17  Short offline       Aborted by host               90%      5637         -
#18  Short offline       Aborted by host               90%      5636         -
#19  Short offline       Aborted by host               90%      5633         -
#20  Short offline       Aborted by host               90%      5633         -
#21  Short offline       Aborted by host               90%      5517         -

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



anyone got any idea what the source of the slowness is, or what programs i can use to find out?

thanks in advance,
Amber

---

### Post by cyberdork33 on 2008-08-10
sorry not directly related to the question, but having your root (bootable) partition on sda5 will not work if you are keeping the GPT partition scheme, and if you are notgoing to keep GPT then there is no reason to keep the EFI partition at the beginning.

---

### Post by AmberWillow on 2008-08-10
Why would this not work? its booting purrfectly..
I left the EFI cause i wasnt sure what would happen if i deleted it, if it would cause problems with booting and bootcamp.

---

### Post by cyberdork33 on 2008-08-10
> **AmberWillow said:**
> Why would this not work? its booting purrfectly..
I left the EFI cause i wasnt sure what would happen if i deleted it, if it would cause problems with booting and bootcamp.
then you must have reformatted with the MBR format rather than a GPT.

the MBR partition table that is 'emulated' when you have a GPT disk is limited to 4 partitions, so it cannot boot "legacy" operating systems on partitions > sda4. No biggie though, but you do not need the EFI partition.... that is only used to perform firmware updates, which you have to have a GPT disk and OS X for...

---

### Post by AmberWillow on 2008-08-11
ok sure.. i guess i can see that.. but that still leaves me with a major performance problem that was already there during the format. Are there no tools for linux that thoroughly check the intergrity of the disk?

I've tried using spinrite from a boot CD but as soon as the interface starts there, the keyboard stopped working.. (same in grub btw, anyone know if there's a fix for that?)

---

### Post by cyberdork33 on 2008-08-11
> **AmberWillow said:**
> ok sure.. i guess i can see that.. but that still leaves me with a major performance problem that was already there during the format. Are there no tools for linux that thoroughly check the intergrity of the disk?Not sure. Apparently the DMA errors are normal for certain SATA hard drives... Can you boot from the LiveCD and run those hdparm commands and such? That should let us know if it is something particular to your install or not. (Also, please use the [ code ] tags to post the output. This will help it retain it's readability.)

> **AmberWillow said:**
> I've tried using spinrite from a boot CD but as soon as the interface starts there, the keyboard stopped working.. (same in grub btw, anyone know if there's a fix for that?)This problem was fixed on the white iMacs with a firmware update, but it is still a problem for aluminum imacs and the aluminum keyboard. The best thing to try is unplug other USB devices, or try another keyboard. Sorry.

---

### Post by AmberWillow on 2008-08-11
currently from the live CD:
```

ubuntu@ubuntu:/var/lock$ sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 488397168, start = 0

```

smartctl is not running from livecd..
and bonnie takes 5 hours to run, AND is not on the livecd..

i do remember i got the message that it was running udma7 before.. cant figure out why thats not coming up anymore...

---

### Post by AmberWillow on 2008-08-11
well.. found the source (and end) of my problems with performance.. the mac was seriously overheated.. 

RIP.. :(

---

