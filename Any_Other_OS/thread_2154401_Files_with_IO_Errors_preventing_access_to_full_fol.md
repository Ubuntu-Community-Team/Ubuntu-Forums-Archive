---
title: "Files with I/O Errors preventing access to full folders?"
date: 2013-06-14
forum: Any Other OS
---

### Post by SineSpe on 2013-06-14
So I just recently had my computer's harddrive crap out on me in the process of trying to relocate my files to an external harddrive. Since i cannot boot Win 7 from my HDD, I'm using Xubuntu 12.10 from a CD to boot. 

When trying to move my files to an external hard drive, i receive the error **"Error when getting information for file '/media/...xxx.mp3' **(or whatever the file happens to be) and it's detailed as an **"Input/output error."**

There's no doubt that this is due to bad sectors on the disk. When commanding dmesg, i receive:

```
end_request: I/O error, dev sda, sector 50748707
Buffer I/O error on device sda3, logical block 2493348
ata1: EH complete
```

Thing is, these bad sectors are also preventing me from opening folders. If i try to open a folder with a bad document *directly* in it (not in a subfolder), an error message displays **"Failed to open directory "Folder"** and it's because of the bad file. 

I need a way to get into these folders to transfer all the files that aren't effected by the bad sectors. My second goal is to repair the damaged files if necessary.

I've already created and saved a 278GB image.dd using Testdisk onto my 1TB external. I was told i could go back to this if anything were to go wrong when trying to repair the original files. However, after completing the image, i received:

```
Image created successfully but read errors have occurred.
```

What are the next steps i should take? The only thing i can think of is running a chkdsk on the original harddrive, but i'm still hesitant as to how to go about doing this.

If there's anymore information you need, let me know. My vocabulary with this stuff is pretty limited.

---

### Post by NikTh on 2013-06-14
So this is a NTFS filesystem partition, correct ? A Windows partition. Well, would be better to run chkdsk from a Windows machine to correct the NTFS filesystem.

Also a Linux utility exist to correct NTFS filesystems , but I would be trust more the MS tool for such job. But if you want to try, the utility's name is ntfs-3g. 
```
sudo apt-get install ntfs-3g 
sudo ntfsfix /dev/sd?? 
``` 

Where ? , replace it with the drive letter and partition letter. (e.g /dev/sda2) 

You can find drive letter and partition letter with ```
sudo fdisk -l
``` 
you will see the HPFS/NTFS filesystem. 

Again, better would be to boot from a Windows CD/DVD and try to correct the filesytem with chkdsk .

Thanks

---

### Post by SineSpe on 2013-06-14
Now i do have a Windows 7 reinstallation disc, but when i try to boot from it, it goes to the process of installing Windows. Is there anyway i can simply boot from this disc without reinstalling? It's necessary for me to boot from a disc or something other than my harddrive because the system will run too slowly working from my harddrive.

I'd much rather use chkdsk, because i've read that ntfs-3g might not be able to get everything that chkdsk would.

---

### Post by NikTh on 2013-06-15
The appropriate forums about Windows 7 are here: [http://www.sevenforums.com/tutorials/433-disk-check.html](http://www.sevenforums.com/tutorials/433-disk-check.html)

You will find several helpful topics. I would prefer to ask there for a Windows problem, rather than here.

---

### Post by oldos2er on 2013-06-15
Moved to Other OS/Distro Support.

---

### Post by mips on 2013-06-15
> **NikTh said:**
> So this is a NTFS filesystem partition, correct ? A Windows partition. Well, would be better to run chkdsk from a Windows machine to correct the NTFS filesystem.

Do NOT run chkdsk on a drive with bad sectors, it will just make things worse.

---

### Post by SineSpe on 2013-06-15
> **mips said:**
> Do NOT run chkdsk on a drive with bad sectors, it will just make things worse.

That's what i've heard, which is why i'm trying to be cautious and also made the image.dd in advance. 
What do you recommend i do in order to access and transfer the GOOD files from the folders that refuse to open?

---

### Post by NikTh on 2013-06-16
> **mips said:**
> Do NOT run chkdsk on a drive with bad sectors, it will just make things worse.

LoL.. 

and what you suggest? 

I know only chkdsk as a powerful tool and the one (MS official) to correct such errors.  I've ran it twice. Well, the truth is that the first time (external HDD) I've lost all of my files. The second time though (internal HDD), everything went well and the problems have been corrected properly.

---

### Post by varunendra on 2013-06-16
> **SineSpe said:**
> That's what i've heard, which is why i'm trying to be cautious and also made the image.dd in advance. 
What do you recommend i do in order to access and transfer the GOOD files from the folders that refuse to open?

I would recommend to run **photorec** on the saved image file to salvage whatever files were accessible (possibly ignoring filesystem errors) at the time you created the image. If the state of the physical drive is not getting worse with every use (that is, the errors are not due to physical wear & tear), you should be good to do it on the drive itself. But in case of doubts, I'd recommend to work on the image.

Using photorec or testdisk on the image file is a read-only operation, so it will not affect the image. It is as easy as using them on the physical drive. So go with whatever you prefer.

If using image, I *think the appropriate command will be -
```
sudo photorec <path to your image.dd>
```

Photorec step-by-step : [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by mips on 2013-06-16
> **SineSpe said:**
> That's what i've heard, which is why i'm trying to be cautious and also made the image.dd in advance. 
What do you recommend i do in order to access and transfer the GOOD files from the folders that refuse to open?

Some things might already not be possible to recover.

Create an image file of the drive or partition using [GNU ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html") and ensure you enable the log file. Once you have an image you can mount it and try to recover from it. You can also use tools like testdisk/photorec on the image.

You can also have a look at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Do me a favour and post the S.M.A.R.T. info for the drive here, you can get that info using the **smartctl** command or you can use a gui called **GSmartControl**.

---

### Post by SineSpe on 2013-06-18
I downloaded Testdisk and Photorec to my new computer with Windows 7 and am trying to read it from there. When running, i receive:

```
Select a media <use Arrow keys, then press Enter>:
>Disk /dev/sda - 1000GB / 931 GiB <RO> - TOSHIBA

>[Proceed] [Quit]
```

I click proceed, and this is where the step-by-step somewhat loses me. I receive:

```
 Partition                  Start        End    Size in sectors
  No partition             0   0  1 121601  80 63 1953525168 [Whole disk]
* HPFS - NTFS              0  32 33    25 126 37     407552 [SYSTEM]
P HPFS - NTFS             25 126 38 118858  49 39 1909047296
P HPFS - NTFS          118858  49 40 121588  24 36   43855872 [Recovery]
P FAT32 LBA            121588  24 37 121601  25 24     208896 [HP_TOOLS]

>[Search] [Options] [File Opt] [Quit]
```

 My image.dd file is no longer on my external harddrive, and now in a folder on this new computer's internal. What are the next steps I should take?

---

### Post by varunendra on 2013-06-18
> **SineSpe said:**
>  My image.dd file is no longer on my external harddrive, and now in a folder on this new computer's internal. What are the next steps I should take?

Running photorec or testdisk without parameters will make them work only on the physical drives. To make it work on the image, you have to run it with the path to the image as its option, like I posted in post #9 earlier (it was for Ubuntu however).

For example, if the path of the **photorec_win.exe** program (that you double-click to run it) is "**D:\testdisk_xyz\win\photorec_win.exe**", the path of the "**image.dd**" file is "**E:\backup\image.dd**", you will have to run photorec from command prompt as -
```
cd D:\testdisk_xyz\win
photorec_win.exe E:\backup\image.dd
```
This will start photorec with the image file instead of your physical drive. The rest of the options will be same as with physical drive.

**PS:**
I have personally found testdisk/photorec to work better when running on Linux. So if you can use it on a Live session (preferably Live usb to save settings), try that instead.

---

### Post by SineSpe on 2013-06-18
So right now, i believe Photorec is running. I've attached a screenshot of that progress to this post.

> **mips said:**
> Some things might already not be possible to recover.

Create an image file of the drive or partition using [GNU ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html") and ensure you enable the log file. Once you have an image you can mount it and try to recover from it. You can also use tools like testdisk/photorec on the image.

You can also have a look at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Do me a favour and post the S.M.A.R.T. info for the drive here, you can get that info using the **smartctl** command or you can use a gui called **GSmartControl**.

This is the SMART information i received by commanding **sudo smartctl --all /dev/sda3** :

```
xubuntu@xubuntu:~/Desktop$ sudo smartctl --all /dev/sda3
smartctl 5.43 2012-06-30 r3573 [i686-linux-3.5.0-17-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.6
Device Model:     ST9320325AS
Serial Number:    5VD1X5P9
LU WWN Device Id: 5 000c50 0217228f7
Firmware Version: 0003DEM1
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Jun 18 22:56:16 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  99) minutes.
Conveyance self-test routine
recommended polling time:      (   3) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   110   074   006    Pre-fail  Always       -       27781091
  3 Spin_Up_Time            0x0003   099   097   085    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   097   097   020    Old_age   Always       -       3277
  5 Reallocated_Sector_Ct   0x0033   089   089   036    Pre-fail  Always       -       243
  7 Seek_Error_Rate         0x000f   081   060   030    Pre-fail  Always       -       4459252319
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6607
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   020    Old_age   Always       -       3175
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       65535
188 Command_Timeout         0x0032   100   001   000    Old_age   Always       -       17180199630
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   059   037   045    Old_age   Always   In_the_past 41 (0 255 42 25 0)
191 G-Sense_Error_Rate      0x0032   098   098   000    Old_age   Always       -       4097
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       5
193 Load_Cycle_Count        0x0032   075   075   000    Old_age   Always       -       50757
194 Temperature_Celsius     0x0022   041   063   000    Old_age   Always       -       41 (0 9 0 0 0)
195 Hardware_ECC_Recovered  0x001a   050   045   000    Old_age   Always       -       27781091
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       423
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       423
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       3
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       224558070110496
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3087503864
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2345006459
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 3280 (device log contains only the most recent five errors)
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

Error 3280 occurred at disk power-on lifetime: 6591 hours (274 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      05:40:41.201  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:41.193  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:41.179  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:41.169  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:41.158  READ FPDMA QUEUED

Error 3279 occurred at disk power-on lifetime: 6591 hours (274 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      05:40:22.878  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      05:40:22.876  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      05:40:22.875  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      05:40:22.874  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      05:40:22.874  READ NATIVE MAX ADDRESS EXT

Error 3278 occurred at disk power-on lifetime: 6591 hours (274 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      05:40:19.848  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:19.485  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:19.464  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:19.464  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:19.067  READ FPDMA QUEUED

Error 3277 occurred at disk power-on lifetime: 6591 hours (274 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      05:40:00.205  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:00.183  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:00.162  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:00.139  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      05:40:00.117  READ FPDMA QUEUED

Error 3276 occurred at disk power-on lifetime: 6591 hours (274 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      05:39:54.112  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      05:39:54.111  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      05:39:54.110  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      05:39:54.109  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      05:39:54.109  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      6564         50765010
# 2  Short offline       Completed without error       00%      5051         -
# 3  Short offline       Completed without error       00%      4914         -
# 4  Short offline       Completed without error       00%      4761         -
# 5  Short offline       Completed without error       00%      4321         -
# 6  Short offline       Completed without error       00%      4232         -
# 7  Short offline       Completed without error       00%      4070         -
# 8  Short offline       Completed without error       00%      3890         -
# 9  Short offline       Completed without error       00%      3698         -
#10  Short offline       Completed without error       00%      3454         -
#11  Short offline       Completed without error       00%      3199         -
#12  Short offline       Completed without error       00%      3157         -
#13  Short offline       Completed without error       00%      3125         -
#14  Short offline       Completed without error       00%      2947         -
#15  Short offline       Completed without error       00%      2730         -
#16  Short offline       Aborted by host               60%      2558         -
#17  Short offline       Completed without error       00%      2164         -
#18  Short offline       Aborted by host               90%      2164         -
#19  Short offline       Completed without error       00%      1909         -
#20  Short offline       Completed without error       00%         0         -

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

### Post by SineSpe on 2013-06-18
Now the estimated time to completion is at about 112 hours. The amount of files found hasn't increased from 32,147 within the past couples hours, and the program keeps returning to read this one sector 19870288. 

I've read that the program may think a file is too small and is returning to that sector to see if any pieces fit, or something to that nature. Can anyone elaborate more on this for me? What's going on in my case, and is waiting the only solution? Thank you.

---

### Post by varunendra on 2013-06-18
> **SineSpe said:**
> Now the estimated time to completion is at about 112 hours. The amount of files found hasn't increased from 32,147 within the past couples hours, and **[COLOR="#FF0000"]the program keeps returning to read this one sector 19870288.[/COLOR]**

I've never experienced that myself, nor have any idea why this could be happening.

When it returns, does it sequentially increase again (with same speed)? If so, it is hopeless. Stop it and try the following if possible (or leave it running if there is some hopeful progress).

Although if you "Stop" the recovery process, photorec is supposed to prompt you to "resume" from where it left when you stopped it (only one time, if you choose "No", it won't ask on next run), but I'm not very certain of that.

* If the image was divided in partitions, you may choose to scan individual partitions to divide the job. Unfortunately, there is no other way to tell photorec to do a partial scan of a drive (apart from choosing to scan only "free space" which is helpful in recovering deleted files).

* Otherwise, you may choose to 'exclude' certain file types which you are not interested in, hoping it may help skipping some problematic blocks. But I'm not sure if it will promp you to 'resume' if settings are changed.

FWIW, I recently recovered data (selecting only pictures and video formats) from a physically crashed 320 GB hard disk in about 19 hours ! That was, in my experience, way too slow than I normally expect. But then again, "Get Data Back" (a top notch commercial tool from runtime software) took even longer with no better results.

---

### Post by SineSpe on 2013-06-18
> **varunendra said:**
> 
* If the image was divided in partitions, you may choose to scan individual partitions to divide the job. Unfortunately, there is no other way to tell photorec to do a partial scan of a drive (apart from choosing to scan only "free space" which is helpful in recovering deleted files).

* Otherwise, you may choose to 'exclude' certain file types which you are not interested in, hoping it may help skipping some problematic blocks. But I'm not sure if it will promp you to 'resume' if settings are changed.

FWIW, I recently recovered data (selecting only pictures and video formats) from a physically crashed 320 GB hard disk in about 19 hours ! That was, in my experience, way too slow than I normally expect. But then again, "Get Data Back" (a top notch commercial tool from runtime software) took even longer with no better results.

I found one person's account of having a similar problem to this and this was their take on it: "..the explanation is probably this: After each file Photorec finds it is  trying to piece together a large previously found fragment with whatever  comes after the newly found file. This means the large file fragment is  read over and over again and only a small fraction of the time is spent  reading new data. Does this explanation seem reasonable?"

This person said that eventually, Photorec completed its business with the one sector and was able to continue reading files normally. I might leave it overnight and see what it does. Regardless...

How would i have Photorec extract only the files with, say, picture,  video, audio and word formats? Keep in mind, there are apparent "read  errors" on the image, so i'm guessing this would be why i'm having a  problem with this sector.

---

### Post by varunendra on 2013-06-19
> **SineSpe said:**
> How would i have Photorec extract only the files with, say, picture,  video, audio and word formats? Keep in mind, there are apparent "read  errors" on the image, so i'm guessing this would be why i'm having a  problem with this sector.

Yes, I remember the image had read errors, that's why I asked if the progress was linear with same speed each time it falls back or jumps to newer sectors (or in a faster speed).

The filter to look for specific file-types only has to be enabled before starting the scan. Since you seem to have made quite some progress now, I think you should leave it going as it is.

The setting is under "Options" by the way (described in the step-by-step guide)

---

### Post by SineSpe on 2013-06-19
> **varunendra said:**
> Yes, I remember the image had read errors, that's why I asked if the progress was linear with same speed each time it falls back or jumps to newer sectors (or in a faster speed).

The filter to look for specific file-types only has to be enabled before starting the scan. Since you seem to have made quite some progress now, I think you should leave it going as it is.

The setting is under "Options" by the way (described in the step-by-step guide)

When it falls back to the weird sector, it does take quite a bit longer than when moving on the the next sector. I'd say it will only read the next sector for a few seconds until it falls back again.

I've had the scan going for 13 hours now. Within the first two hours, i reached this weird sector, and after 11 additional hours, no new files have been recovered. I'm stuck around 32,147 files and an estimated time of 377 hours. I think what i'll do is leave it going overnight (about another 8 hours or so). If it's still getting hung up on this sector, I'll save what i have, start over and have Photorec only recover images, videos, audio, documents, i suppose. There's really no need for me to recover things i'm not looking to keep. 

If by the time i start over, we can find **a way to skip/ignore these weird sectors**, that would be great, in case the process gets caught up again.

---

### Post by mips on 2013-06-19
> **SineSpe said:**
> 
This is the SMART information i received by commanding **sudo smartctl --all /dev/sda3** :


1. That drive is shot/broken.
2. You're image you have of 278GB is not complete, dd does not work well with bad sectors/faulty drives. You're missing about 40GB of data.
3.  See post#10 again wrt GNU ddrescue, [COLOR=#ff0000]**make sure you use a log file see the flag settings**[/COLOR]. Run it in the forward direction (normal) and when it starts picking up errors run it in reverse until it hits errors. Next run it in the forward direction again and let it do it's job. Read the documentation and subscribe to the mailing list if you have questions or need help. It's a very powerful tool. Only image the faulty partition you need to get data from and not the entire drive (assuming you have multiple partitions).

Right now you are wasting your time working on a incomplete image.
[COLOR=#000000][/COLOR]

---

### Post by SineSpe on 2013-06-19
> **mips said:**
> 1. That drive is shot/broken.
2. You're image you have of 278GB is not complete, dd does not work well with bad sectors/faulty drives. You're missing about 40GB of data.
3.  See post#10 again wrt GNU ddrescue, [COLOR=#ff0000]**make sure you use a log file see the flag settings**[/COLOR]. Run it in the forward direction (normal) and when it starts picking up errors run it in reverse until it hits errors. Next run it in the forward direction again and let it do it's job. Read the documentation and subscribe to the mailing list if you have questions or need help. It's a very powerful tool. Only image the faulty partition you need to get data from and not the entire drive (assuming you have multiple partitions).

Right now you are wasting your time working on a incomplete image.


That's disappointing news considering that when i woke up, Photorec had worked its way past the weird sector. It's completed now with about 219,219 files. There's no harm in continuing to try, having the time.

> **mips said:**
> Create an image file of the drive or partition using [GNU ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html")  and ensure you enable the log file. Once you have an image you can  mount it and try to recover from it. You can also use tools like  testdisk/photorec on the image.

You can also have a look at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I'll see what I can do regarding GNU ddrescue. Will i need Lzip as well, or can i do without? In the meantime, out of curiosity, what feedback from Gsmartctl told you the hard drive was shot?

EDIT: Also, i'm kind of stumped on how to get this program to work. I've downloaded the ddrescue 1.16 files and extracted them from the index ([http://mirror.anl.gov/pub/gnu/ddrescue/](http://mirror.anl.gov/pub/gnu/ddrescue/)), but i'm not sure where to go from here. Will the program work if on a USB, since my old computer is running from CD?

---

### Post by varunendra on 2013-06-19
> **mips said:**
> 2. You're image you have of 278GB is not complete, dd does not work well with bad sectors/faulty drives. You're missing about 40GB of data.
3.  See post#10 again wrt GNU ddrescue....
Although I wouldn't consider an incomplete image necessarily a big problem IF the missing part was only bad blocks (they won't add any value anyway) or the end of the partition/drive (of course costing some files though), I would certainly +1 to GNU ddrescue after what I read about its imaging capabilities recently. In ubuntu repository, it is available as package gddrescue (sudo apt-get install gddrescue). I can't comment on the role or necessity of Lzip though, but it doesn't seem necessary (guessing by the fact that it would have been a dependency of the package otherwise).

However -
> **SineSpe said:**
> That's disappointing news considering that when i woke up, Photorec had worked its way past the weird sector. It's completed now with about 219,219 files. There's no harm in continuing to try, having the time.
That's sounds like a very good news to me, IF it doesn't encounter another problem block like that.

As far as I could gather, gddrescue seems to be only meant for imaging a disk/partition. You'll have to run data-recovery tools like photorec anyway to recover lost files. So, given that it has made progress now, I'd suggest to let it finish its current task or at least allow it to run as long as you can. You can do the file-check on the files it has recovered so far in the parallel while it is working. So that should help deciding whether they are worth letting it continue or not (some files may be incomplete/corrupt, some should be intact).

---

### Post by SineSpe on 2013-06-19
> **varunendra said:**
> I would certainly +1 to GNU ddrescue after what I read about its imaging capabilities recently. In ubuntu repository, it is available as package gddrescue (**sudo apt-get install gddrescue**). I can't comment on the role or necessity of Lzip though, but it doesn't seem necessary (guessing by the fact that it would have been a dependency of the package otherwise).

As far as I could gather, gddrescue seems to be only meant for imaging a disk/partition. You'll have to run data-recovery tools like photorec anyway to recover lost files. So, given that it has made progress now, I'd suggest to let it finish its current task or at least allow it to run as long as you can. 

It finished this morning with 219,219 files. I've have anti-virus software running and it caught a few viruses that Photorec resurrected. 

In the meantime, I'll just do the **sudo apt-get install gddrescue **on my old computer that's booting from CD. After i install it, i'm guessing the command i'll have to use is..

```
 sudo ddrescue  /dev/sda3 /dev/hdb logfile
```

But i'm also worried about the warnings:
1. "IMPORTANT! Never try to rescue a r/w mounted partition. The resulting copy may be useless."
2. "IMPORTANT! If you use a device or a partition as destination, any data stored there will be overwritten."
3. "IMPORTANT! Never try to repair a file system on a drive with I/O errors; you will probably lose even more data."

 
1. How do i know if my partition is r/w or not?
2. Since i'll be using my external as my destination, i'll have to back up all the files Photorec recovered so that's not much of a problem.
3. I/O errors seem to be one of the most evident issues with my harddrive. Will i be okay with ddrescue as long as i don't attempt to "repair"? Is this why people may advise against repairing with chkdsk?

---

### Post by mips on 2013-06-19
1. The partition should not be mounted from what I recall.
2. Why are you specifying a partition instead of an image file?
3. Yes that makes sense.

As to how I know your drive is shot I looked at the Reallocated_Sector_Ct, Current_Pending_Sector, Offline_Uncorrectable values and that's more than enough to see that the drive is on it's way out.

---

### Post by mips on 2013-06-19
> **varunendra said:**
> Although I wouldn't consider an incomplete image necessarily a big problem IF the missing part was only bad blocks (they won't add any value anyway) or the end of the partition/drive (of course costing some files though)...


I would agree but we are only speculating as to whether there is important data there or not. Thing is with dd it usually crpas out out when encountering bad sectors so if that's at the beginning of the 'bad' area and you have data there then you are going to lose out. Also 600 odd bad sectors does not equate to 40GB of data so there is definitely something amiss here.

---

### Post by varunendra on 2013-06-20
> **mips said:**
> I would agree but we are only speculating as to whether there is important data there or not.
....Also 600 odd bad sectors does not equate to **40GB** of data so there is definitely something amiss here.
I totally agree.

One thing I was wondering about (not that it makes it any less important), aren't you miscalculating the size? 320 GB declared by vendors is actually 298GB in binary (GiB) that computer sees. Since the image size is about 278 GiB as per OP (or 283 GiB as reported by PhotoRec in the screenshot in post #13), the difference is about **20 GiB**, not 40.

Although it still is a lot of data, and a lot of room for possible further problems.


@ SineSpe,
To elaborate what mips said regarding point #2, your command be something like -
```
sudo ddrescue  [COLOR="#FF0000"]/dev/sda3[/COLOR] [COLOR="#006400"]/media/<backup path>/image2[/COLOR] [COLOR="#0000CD"]logfile[/COLOR]
```
where -
[INDENT]*** [COLOR="#FF0000"]/dev/sda3[/COLOR]** is the partition you want to create image of (it should not be mounted)

*** [COLOR="#006400"]/media/<backup path>/image2[/COLOR]** is the path and name of the 'image file' that you will be creating from the partition. All the mounted partitions (internal or an external hdd) are mounted in /media/ in Ubuntu, hence the /media/ part.

*** [COLOR="#0000CD"]logfile[/COLOR]** is what it says - the file that will keep log of the progress. Back it up before repeating operations, just in case..[/INDENT]

---

### Post by mips on 2013-06-20
> **varunendra said:**
> I totally agree.

One thing I was wondering about (not that it makes it any less important), aren't you miscalculating the size? 320 GB declared by vendors is actually 298GB in binary (GiB) that computer sees. Since the image size is about 278 GiB as per OP (or 283 GiB as reported by PhotoRec in the screenshot in post #13), the difference is about **20 GiB**, not 40.


Yes that would be correct, I never converted the claimed size to actual size. 20GB is still a lot and way more than 600 bad sectors.

---

### Post by SineSpe on 2013-06-20
> **varunendra said:**
> 
@ SineSpe,
To elaborate what mips said regarding point #2, your command be something like -
```
sudo ddrescue  [COLOR=#FF0000]/dev/sda3[/COLOR] [COLOR=#006400]/media/<backup path>/image2[/COLOR] [COLOR=#0000CD]logfile[/COLOR]
```
where -[INDENT]*** [COLOR=#FF0000]/dev/sda3[/COLOR]** is the partition you want to create image of (it should not be mounted)

*** [COLOR=#006400]/media/<backup path>/image2[/COLOR]** is the path and name of the 'image file' that you will be creating from the partition. All the mounted partitions (internal or an external hdd) are mounted in /media/ in Ubuntu, hence the /media/ part.

*** [COLOR=#0000CD]logfile[/COLOR]** is what it says - the file that will keep log of the progress. Back it up before repeating operations, just in case..
[/INDENT]


Okay, so the backup path would just be the path to my external hard drive, correct? If i specify **/media/<backup path>/image2 **rather than **/media/<backup path>**, is it safe to say that the data on my external won't be overwritten? And how can i tell if my internal hard drive is unmounted?

---

### Post by varunendra on 2013-06-20
> **SineSpe said:**
> Okay, so the backup path would just be the path to my external hard drive, correct? If i specify **/media/<backup path>/image2 **rather than **/media/<backup path>**, is it safe to say that the data on my external won't be overwritten?
Yes, the backup image will be a file (image2) on the backup partition. For example, if the external drive is "**/dev/sdb1**" and is mounted as "**/media/FreeAgentGo/**", then the backup path can be - "**/media/FreeAgentGo/image2**". Or, if you want it in some folder named "BackupImage" (already existing, or you must create it beforehand) on the backup partition, then "/media/FreeAgentGo/BackupImage/Image2".

> And how can i tell if my internal hard drive is unmounted?
Run the "**mount**" command.
It will show all the mounted filesystems. Make sure your source partition is not one of them. If it is, un-mount it from within nautilus (or whatever file manager you have), or with the command -
```
sudo umount /dev/**[COLOR="#FF0000"]sda3[/COLOR]**
```
..assuming that **/dev/[COLOR="#FF0000"]sda3[/COLOR]** is the source partition which you have to create image of.

Being based on the "dd" command itself, I think ddrescue can be equally dangerous if used incorrectly. So feel free to ask here before executing it if you have any confusions.

---

### Post by SineSpe on 2013-06-20
> **varunendra said:**
> Yes, the backup image will be a file (image2) on the backup partition. For example, if the external drive is "**/dev/sdb1**" and is mounted as "**/media/FreeAgentGo/**", then the backup path can be - "**/media/FreeAgentGo/image2**". Or, if you want it in some folder named "BackupImage" (already existing, or you must create it beforehand) on the backup partition, then "/media/FreeAgentGo/BackupImage/Image2".


Run the "**mount**" command.
It will show all the mounted filesystems. Make sure your source partition is not one of them. If it is, un-mount it from within nautilus (or whatever file manager you have), or with the command -
```
sudo umount /dev/**[COLOR=#FF0000]sda3[/COLOR]**
```
..assuming that **/dev/[COLOR=#FF0000]sda3[/COLOR]** is the source partition which you have to create image of.

Being based on the "dd" command itself, I think ddrescue can be equally dangerous if used incorrectly. So feel free to ask here before executing it if you have any confusions.

So i suppose my full process will be to run **mount**; if dev/sda3 is listed, i'll run **sudo umount /dev/sda3**
I'll then install GNU ddrescue with [B]sudo apt-get install gddrescue 
[/B]I'll then run the program with[B] sudo ddrescue  [COLOR=#FF0000]/dev/sda3[/COLOR] [COLOR=#006400]/media/<backup path>/image2[/COLOR] [COLOR=#0000CD]logfile
[/COLOR]
[/B]I'll just have to determine the path of my external. What are the things ddrescue have done if used improperly?

---

### Post by varunendra on 2013-06-20
> **SineSpe said:**
> So i suppose my full process will be to run **mount**; if dev/sda3 is listed, i'll run **sudo umount /dev/sda3**
I'll then install GNU ddrescue with [B]sudo apt-get install gddrescue 
[/B]I'll then run the program with[B] sudo ddrescue  [COLOR=#FF0000]/dev/sda3[/COLOR] [COLOR=#006400]/media/<backup path>/image2[/COLOR] [COLOR=#0000CD]logfile
[/COLOR]
[/B]
Looks perfect to me.

> What are the things ddrescue have done if used improperly?
If you reverse the source and destination, and if the source (after reversing) is an existing image file or partition, the destination (your problem partition) will get overwritten without warning.

If the source is okay, but the destination is an existing file, it will get overwritten (not in the second or subsequent runs when the logfile has been created).

These are the only risks I can think of in the above mentioned process. But I have never used ddrescue myself so am just guessing.

---

### Post by SineSpe on 2013-06-21
> **varunendra said:**
> Looks perfect to me.

If you reverse the source and destination, and if the source (after reversing) is an existing image file or partition, the destination (your problem partition) will get overwritten without warning.

If the source is okay, but the destination is an existing file, it will get overwritten (not in the second or subsequent runs when the logfile has been created).

These are the only risks I can think of in the above mentioned process. But I have never used ddrescue myself so am just guessing.

OH! If i wanted to ddrescue a specific folder, would that be at all possible? Some folders in my libraries are all i'm really worried about.

---

### Post by varunendra on 2013-06-21
At the risk of commenting on a software that I haven't used personally, I don't think it is possible for ddrescue.

It is a disk/partition imaging software, not a data recovery one. I don't think it even looks at directory structure. In the form of a partition, you just tell it a starting and ending cylinder, then all it does is to somehow copy all the blocks/sectors in-between, without caring or analyzing what those blocks contain.

What you are asking for is the job of data recovery software and it can be done reliably only if the partition table itself is intact (I'm not sure about that in your case). If the majority of the content on the partition can be read without errors, then I would assume that the partition table is good, and you may try programs like "scrounge-ntfs" (only for ntfs partitions) or "safecopy" to try recovering files ignoring errors. Both these programs are available in Ubuntu repositories. All of these software can be run on either the partition itself, or more safely, on the mounted image that you are creating with ddrescue.

---

### Post by mips on 2013-06-21
> **SineSpe said:**
> OH! If i wanted to ddrescue a specific folder, would that be at all possible?

No. You can only image partitions & drives.

---

### Post by SineSpe on 2013-06-21
> **varunendra said:**
> At the risk of commenting on a software that I haven't used personally, I don't think it is possible for ddrescue.

It is a disk/partition imaging software, not a data recovery one. I don't think it even looks at directory structure. In the form of a partition, you just tell it a starting and ending cylinder, then all it does is to somehow copy all the blocks/sectors in-between, without caring or analyzing what those blocks contain.

What you are asking for is the job of data recovery software and it can be done reliably only if the partition table itself is intact (I'm not sure about that in your case). If the majority of the content on the partition can be read without errors, then I would assume that the partition table is good, and you may try programs like "scrounge-ntfs" (only for ntfs partitions) or "safecopy" to try recovering files ignoring errors. Both these programs are available in Ubuntu repositories. All of these software can be run on either the partition itself, or more safely, on the mounted image that you are creating with ddrescue.

If running those programs will wear down my internal through from excess use, i'll go ahead and create the image then see what i can do with it regarding those programs.

---

### Post by varunendra on 2013-06-21
That's a good idea. The very purpose of creating images like this is to prevent any further loss due to physical wear & tear.

---

### Post by SineSpe on 2013-06-23
I'd like to take a minute and thank everyone who's helped me out this far. Even with the bad sectors, this image.dd has helped me recover years of files and memories that would've been lost to broken hardware. Even if everything isn't salvageable, i'm glad to have recovered as much as these programs did. I feel foolish for pushing my computer so far when it began slowing down months ago, but at least now i'll be able to recognize the signs of a failing harddrive. 

Currently, i'm picking through the files and backing them up to my new computer. Once that's done, i'll clear space on my external for the ddrescue and start with that project.

Thank you all, again O:)

---

### Post by SineSpe on 2013-06-25
So i had an interesting thing happen today.

I was going through the .jpg's that Photorec had recovered on my external when i came across some strange files. When made them strange was that when i tried deleting them, i couldn't because of I/O device errors. The thumbnails and previews of many of these images showed complete parts of the image blacked out and missing. I wasn't surprised because i thought this was to be expected. 

Then i started scrolling down and I could watch the thumbnails of once-normal files become partially blacked out. Does anyone know what is going on with this?

---

### Post by varunendra on 2013-06-26
> **SineSpe said:**
> I was going through the .jpg's that Photorec had recovered on my external when i came across some strange files. When made them strange was that when i tried deleting them, i couldn't because of **[COLOR="#FF0000"]I/O device errors[/COLOR]**.

I/O device errors, as far as I know, are indications of physical errors on the drive. Regardless of how and what kind of files you have copied to the drive, an I/O error should never occur if the drive and its connection are healthy. So try reconnecting the drive, then see if the same error on the same files (or more) occurs again. If so, it is a bad indication, possibly of a failing drive (yet again !!).

By the way, did you try to open the files whose thumbnails seemed blacked out (of earlier healthy files)? Thumbnails do not necessarily represent the actual file always and can be dodgy sometimes, especially when there are hundreds of files in a single folder.

However, if the files are corrupt too (like the thumbnails represent), and you are sure they were healthy earlier, then I'm afraid it is also an indication of a failing drive !

---

### Post by SineSpe on 2013-06-26
> **varunendra said:**
> I/O device errors, as far as I know, are indications of physical errors on the drive. Regardless of how and what kind of files you have copied to the drive, an I/O error should never occur if the drive and its connection are healthy. So try reconnecting the drive, then see if the same error on the same files (or more) occurs again. If so, it is a bad indication, possibly of a failing drive (yet again !!).

By the way, did you try to open the files whose thumbnails seemed blacked out (of earlier healthy files)? Thumbnails do not necessarily represent the actual file always and can be dodgy sometimes, especially when there are hundreds of files in a single folder.

However, if the files are corrupt too (like the thumbnails represent), and you are sure they were healthy earlier, then I'm afraid it is also an indication of a failing drive !

I just bought this drive though a few months ago... I didn't try opening them or anything, just moving them. But it freaked me out so i just shut down my computer, lol.. When i accessed my external hard drive again, it was like nothing happened and all the files were fine. Currently, there was only one image that i've found to show the same repeated error (although i just went looking for it to get a screenshot but only found a clean version of the file so..)

If it occurs again, i'll be sure to report back. Once i've gotten this drive clear of the things i need, i'll format and repair it.

---

### Post by varunendra on 2013-06-26
> **SineSpe said:**
> When i accessed my external hard drive again, it was like nothing happened and all the files were fine.

Like I mentioned earlier, the thumbnails may not always represent the actual state of the files, especially if there are hundreds of them in a single directory.

But this kind of behaviour can also indicate a hardware failure, ranging from a mere loose connection to a failing drive or motherboard (the I/O controller) or memory leakage.

If any weird behaviour occurs again, you should try running "memtest" (Test Memory) option from the live cd/usb for at least 4-6 hours (recommended duration is 24 hours though). It will give you errors if there is a memory leakage problem. It may also freeze in case of a motherboard problem. But can't test the drive or its connection.

---

