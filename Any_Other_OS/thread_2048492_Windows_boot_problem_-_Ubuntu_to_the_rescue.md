---
title: "Windows boot problem - Ubuntu to the rescue?"
date: 2012-08-26
forum: Any Other OS
---

### Post by MontyWest on 2012-08-26
Hi, I hope this is going to be an easy/ interesting one for you Ubuntu experts.

I do all the maintenance for our extended family's pcs which is about 9 all told, all running Windows: XP, Vista and Win7. (The oldest is from 1999 which is still running, but slow!)

Yesterday, I had a first look at my younger sister's 2007 Toshiba running Vista which she has been complaining about and right away I noticed she had 2 anti-virus programs installed: Norton (expired) and Avast. So having updated Avast I set about uninstalling Norton. There were viruses (root kits) previously in the Norton vault that were detected by Avast as Norton was uninstalled. At this point I moved over to help my Dad with his pc and when I came back sister's pc had crashed, would not boot into Windows and was just showing a black screen with a flashing cursor.

After loading Toshiba Bios I just get the black screen with flashing cursor.
F8 does not work. Does not boot into Safe Mode.
F2 goes to Phoenix TrustedCore Setup utility. The hard drive and CD-ROM drive are listed in Main and Boot.

Created System Repair Disc from Windows 7 (64 bit)
F12, select CDROM and press any key to boot from CD
No operating system listed.
Cannot find system image on this computer. 
HDD is Toshiba MK1237GSX-(S1)

Startup repair lasts only 10 seconds or so and finds root problem is 
System volume on disk is corrupt.

chkdsk does not work.

_Windows Memory Diagnostic_
windows cannot check for memory problems. 
An error is preventing windows from checking memory problems during startup. To run the Windows memory diagnostic manually, boot the computer from the windows installation disc, then select windows memory diagnostic from the windows boot manager. Does not work.

_Command Prompt_
sfc /scannow
There is a system repair pending which requires reboot to complete. Restart windows and run sfc again.

_Created Linux Live USB_
This will boot up!
Using File Manager - Dolphin I can see a section called Data with photos and mp3 downloads. Is this the My Documents folder from Windows?

I can also see a 55.8 GiB Hard Drive but 
"An error occured while accessing hard drive, the system responded: the requested operation has failed. Error mounting: mount exited with exit code 18. failed to open $MFT/$BITMAP No such file or directory. Failed to load $MFT: no such file or directory. 
Failed to mount '/dev/sda2': no such file or directory.

By going into root using terminal I can see the HDD is split into 3 elements with sda2 being the boot section.

I am assuming either a virus has caused some damage or part of the HDD has failed (it is certainly a bit noisier than other HDDs but regular users wouldn't notice).

So the questions I have for you guys are:
[1] can I repair the missing or damaged files using Ubuntu? Force it to mount?
a: can I run a anti-virus?
b: can I run a HDD health test?
 
[2] if the HDD cannot be repaired, how do I get all the data off? I have already copied the folders from the Data section onto an external HDD.

---

### Post by linuxman72 on 2012-08-26
I'm no expert, but i think you could run ubuntu off a usb, mount the hard drive(click places bar and scroll down to the hard drives) , and use wine to run an antivirus. However, i don't know if it would detect a virus on windows

---

### Post by MontyWest on 2012-08-26
Thanks, I'll give it a go.

---

### Post by oldfred on 2012-08-26
Moved to other os since Windows issues.

Ubuntu will not mount partitions that need chkdsk to prevent further damage that then chkdsk might not be able to fix. You can only run chkdsk from a Windows repairCD or USB. But I have run chkdsk from a Windows 7 repairUSB on my XP install. But it wrote a Windows 7 partition boot sector (PBR), which then I had to reinstall an XP PBR.

Sometimes testdisk will show info.

I have not tried any of the anti-virus available:

Sites not verified but look useful:
[http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)
[http://www.askvg.com/download-free-bootable-rescue-cds-from-kaspersky-bitdefender-avira-f-secure-and-others/](http://www.askvg.com/download-free-bootable-rescue-cds-from-kaspersky-bitdefender-avira-f-secure-and-others/)
[http://www.techmixer.com/bitdefender-rescue-cd-with-auto-update-virus-definition-features/](http://www.techmixer.com/bitdefender-rescue-cd-with-auto-update-virus-definition-features/)
[http://www.rarst.net/software/drweb-livecd/](http://www.rarst.net/software/drweb-livecd/)
In Ubuntu on USB full install or with persistence:
sudo apt-get clamav

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Sometimes chkdsk may not run if it does not see partition as NTFS:
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
Rebuilding An NTFS Boot Sector On An NTFS Partition 

But with Windows 7 ( and maybe Vista) you still have to repair from Windows 7, as XP and Windows 7 have different PBRs. XP's PBR says to boot with ntldr and Windows 7 says to boot with bootmgr. Testdisk rebuilds a XP style NTFS partition boot sector, but then Windows 7 may see it where before it may not.

Documenting system is also a good idea. And it may highlight errors.

This will not directly fix Windows issues, but we use it to repair grub to boot Windows or reinstall a Windows boot loader to the MBR.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by linuxman72 on 2012-08-26
One thing I forgot to add:

to do this you will need to be using GNOME not unity. to switch, reboot on usb and click the symbol on the upper-lefthand corner of the login box. select gnome and login.

---

### Post by NikTh on 2012-08-26
Hi ,
I think @oldfred covered up everything for the repair and cleaning virus procedure. 

One thing that remains is how healthy is you Disk. 

So when you boot from Ubuntu Live (click "Try Ubuntu") , open a terminal (ctrl+alt+t , combo) and copy-paste from here below commands , one line at time
```
sudo apt-get install smartmontools --no-install-recommends
sudo smartctl -a /dev/sda
``` 
and give here the results of the second command. 

Put the results between the ```
 brackets so can be readable.
[noparse][code]The results here
```[/noparse] 
Thank you.

---

### Post by MontyWest on 2012-08-28
> **NikTh said:**
> Hi ,
I think @oldfred covered up everything for the repair and cleaning virus procedure. 

One thing that remains is how healthy is you Disk. 

So when you boot from Ubuntu Live (click "Try Ubuntu") , open a terminal (ctrl+alt+t , combo) and copy-paste from here below commands , one line at time
```
sudo apt-get install smartmontools --no-install-recommends
sudo smartctl -a /dev/sda
``` 
and give here the results of the second command. 

Put the results between the ```
 brackets so can be readable.
[noparse][code]The results here
```[/noparse] 
Thank you.

Thank you for your replies. I'll start with the easiest first re: above!
Below I have copied the full results of both instructions. This was at second attempt as the first failed due to lack of internet connection which I rectified. I must say at this point how impressed I am with Linux Kubuntu as this is the first time I have used it and I will definitely install it on my oldest pcs which should hopefully make them properly useable again (because of small max RAM).

What is your analysis of these results below?

```
kubuntu@kubuntu:~$ sudo apt-get install smartmontools --no-install-recommends
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  smartmontools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 455 kB of archives.
After this operation, 1315 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main smartmontools i386 5.41+svn3365-1 [455 kB]
Fetched 455 kB in 0s (1418 kB/s)     
Selecting previously unselected package smartmontools.
(Reading database ... 70466 files and directories currently installed.)
Unpacking smartmontools (from .../smartmontools_5.41+svn3365-1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up smartmontools (5.41+svn3365-1) ...
kubuntu@kubuntu:~$ sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-23-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA MK1237GSX
Serial Number:    Y7NUTM0TT
Firmware Version: DL130M
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Aug 28 09:45:54 2012 UTC
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
data collection:                (  120) seconds.
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
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  80) minutes.
SCT capabilities:              (0x0001) SCT Status supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1637
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       2123
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       72
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       10037
 10 Spin_Retry_Count        0x0033   142   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       2063
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       294
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       14670
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       30 (Min/Max 9/63)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       70
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       60
222 Loaded_Hours            0x0032   081   081   000    Old_age   Always       -       7703
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       312
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 2
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

Error 2 occurred at disk power-on lifetime: 3702 hours (154 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 41 a0 70 ff f6 40  Error: ICRC, ABRT at LBA = 0x00f6ff70 = 16187248

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 b0 22 48 ea 40 00      02:26:09.383  WRITE FPDMA QUEUED
  61 18 a8 98 63 ac 40 00      02:26:09.383  WRITE FPDMA QUEUED
  61 10 a0 70 ff f6 40 00      02:26:09.383  WRITE FPDMA QUEUED
  60 08 98 a0 fc 3d 40 00      02:26:09.382  READ FPDMA QUEUED
  60 08 90 08 c6 41 40 00      02:26:09.382  READ FPDMA QUEUED

Error 1 occurred at disk power-on lifetime: 3702 hours (154 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 41 a0 70 ff f6 40  Error: ICRC, ABRT at LBA = 0x00f6ff70 = 16187248

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 b0 22 48 ea 40 00      02:26:09.383  WRITE FPDMA QUEUED
  61 18 a8 98 63 ac 40 00      02:26:09.383  WRITE FPDMA QUEUED
  61 10 a0 70 ff f6 40 00      02:26:09.383  WRITE FPDMA QUEUED
  60 08 98 a0 fc 3d 40 00      02:26:09.382  READ FPDMA QUEUED
  60 08 90 08 c6 41 40 00      02:26:09.382  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         3         -
# 2  Short offline       Completed without error       00%         3         -
# 3  Short offline       Completed without error       00%         3         -
# 4  Short offline       Completed without error       00%         3         -
# 5  Short offline       Completed without error       00%         2         -
# 6  Short offline       Completed without error       00%         2         -
# 7  Short offline       Completed without error       00%         2         -
# 8  Short offline       Completed without error       00%         2         -
# 9  Short offline       Completed without error       00%         2         -
#10  Short offline       Completed without error       00%         1         -
#11  Short offline       Completed without error       00%         1         -
#12  Short offline       Completed without error       00%         1         -
#13  Short offline       Completed without error       00%         1         -

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

### Post by MontyWest on 2012-08-28
@oldfred Thank you for your reply.

AVG Rescue CD
That is a great find and I got the broken laptop to boot into it on USB at first attempt. But after agreeing User Licence Agreement it came up with 
```
-----smartctl reports some problems with disk!-----

/dev/sda:
ATA Error Count: 2
Error 2 occurred at disk power-on lifetime: 3702 hours (154 days + 6 hours)
Error 1 occurred at disk power-on lifetime: 3702 hours (154 days + 6 hours)

<EXIT>
```

This reflects the error timings listed in the results above.

Edit: Exit didn't mean exit! It does go through to Main Menu.
So I'll report results in a little while.

Edit 2: Virus scanning works for /sda1 (NTFS 1.5 G) and /sda3 (NTFS 54.5G) with no infections found.
but /sda2 does not show up in list of volumes for scanning (presumably due to these 2 errors).

Edit 3: In the Utilities Menu is listed:
```
 File Manager    Midnight Commander
TrueCrypt                   Utility for mounting encrypted FS
Registry Editor            Windows Registry editor
Fix MBR                      Write DOS MBR to selected volume
TestDisk                     Disk data recovery utility
Smartctl                     Run disks S.M.A.R.T. test
PhotoRec                   Recover deleted files
Ping                           Ping utility
Links                         Text web browser
```

Useful?

I'll try your next suggestion...

---

### Post by MontyWest on 2012-08-28
Running TESTDISK

Analysis:
```

      Partition                            Start              End          Size in Sectors
1 P Windows RE(store)     0      32  33        191   89  26           3072000
2 * HPFS - NTFS             191     89  27     7477   118  1          117051392
3 P HPFS - NTFS            7477   118   2    14592   190  62       114307072   (data)


* = Primary bootable
```

Edit 1: When doing Quick Search and then P - list files, of the second partition it reports:
```
Can't open filesystem. Filesystem seems damaged.
``` 

Edit 2: It would appear that WinRE (the first partition) is Windows Recovery Environment which is a set of tools also known as System Recovery Options.
Should I change the characteristics so that the laptop boots into this partition?

In the meantime, I read in the step by step:
Repair An NTFS MFT

The MFT (Master File Table) is sometimes corrupted. If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk. In the Advanced menu, select your NTFS partition, choose Boot, then Repair MFT. TestDisk will compare the MFT and MFT mirror (its backup). If the MFT is damaged, it will try to repair the MFT using the backup. If the MFT backup is damaged, it will use the main MFT.

Result ```
 Boot sector
Status: OK

Backup Boot Sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access any data; even if the partition is not bootable.
```

Will edit this as I work through the Step by Step.

---

### Post by NikTh on 2012-08-28
Hi , 
this is a good value 

> **MontyWest said:**
> 
```
1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
```
  but below values are not good at all. 
  > **MontyWest said:**
> ```
 5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       72
 196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       70
```

Take a look here : [http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T). for detailed explanation. 

It is not for sure that HDD will fail , but it is possible enough .
Thank you

---

### Post by kemtnbkr on 2012-08-28
Somewhat unrelated- if you are going to try to revive computers from '99 with Linux, you may want to look into Xubuntu or Lubuntu which are both more lightweight that Kubuntu (less eyecandy).

---

### Post by MontyWest on 2012-08-29
> **kemtnbkr said:**
> Somewhat unrelated- if you are going to try to revive computers from '99 with Linux, you may want to look into Xubuntu or Lubuntu which are both more lightweight that Kubuntu (less eyecandy).

Thanks for the tip.

Mmmmmm, eye candy. :-)

---

### Post by MontyWest on 2012-08-29
_Farbar Recovery Scan Tool _
This program will display detailed information about the Windows Registry loading points, services, driver services, Netsvcs entries, known DLLs, Exe associations, drives, and partition specifications. 

I booted the laptop from the Win7 Repair Disk and ran FRST from the Command Prompt.

Interesting to see what files seem to be missing in the report below. Can they simply be replaced? Here I go once more on another Google marathon. 

```
Scan result of Farbar Recovery Scan Tool Version: 29-08-2012 03
Ran by SYSTEM at 29-08-2012 22:18:44
Running from G:\
   (X64) OS Language: English(US) 
Attention: Could not load system hive.Attention: System hive is missing.

==================== Registry (Whitelisted) ===================

Attention: Software hive is missing.

HKLM\...\Winlogon: [Userinit] 
HKLM-x32\...\Winlogon: [Userinit]  [x]
HKLM\...\Winlogon: [Shell]  [x ] ()
HKLM-x32\...\Winlogon: [Shell]  [x ] ()

==================== Services (Whitelisted) ======


==================== Drivers (Whitelisted) ===================


==================== NetSvcs (Whitelisted) =================


==================== One Month Created Files and Folders ======================

2012-08-29 21:58 - 2012-08-29 21:58 - 00000000 ___AD \Windows\debug


==================== 3 Months Modified Files ================================


==================== Known DLLs (Whitelisted) =================


==================== Bamital & volsnap Check =================

C:\Windows\System32\winlogon.exe IS MISSING <==== ATTENTION!.
C:\Windows\System32\wininit.exe IS MISSING <==== ATTENTION!.
C:\Windows\SysWOW64\wininit.exe IS MISSING <==== ATTENTION!.
C:\Windows\explorer.exe IS MISSING <==== ATTENTION!.
C:\Windows\SysWOW64\explorer.exe IS MISSING <==== ATTENTION!.
C:\Windows\System32\svchost.exe IS MISSING <==== ATTENTION!.
C:\Windows\SysWOW64\svchost.exe IS MISSING <==== ATTENTION!.
C:\Windows\System32\services.exe IS MISSING <==== ATTENTION!.
C:\Windows\System32\User32.dll IS MISSING <==== ATTENTION!.
C:\Windows\SysWOW64\User32.dll IS MISSING <==== ATTENTION!.
C:\Windows\System32\userinit.exe IS MISSING <==== ATTENTION!.
C:\Windows\SysWOW64\userinit.exe IS MISSING <==== ATTENTION!.
C:\Windows\System32\Drivers\volsnap.sys IS MISSING <==== ATTENTION!.

==================== EXE ASSOCIATION =====================

HKLM\...\.exe:  <===== ATTENTION!
HKLM\...\exefile\DefaultIcon:  <===== ATTENTION!
HKLM\...\exefile\open\command:  <===== ATTENTION!

==================== Restore Points  =========================


==================== Memory info =========================== 

Percentage of memory in use: 21%
Total physical RAM: 2038.4 MB
Available physical RAM: 1604.44 MB
Total Pagefile: 2038.4 MB
Available Pagefile: 1589.78 MB
Total Virtual: 8192 MB
Available Virtual: 8191.9 MB

==================== Partitions ============================

1 Drive d: (Data) (Fixed) (Total:54.51 GB) (Free:42.05 GB) NTFS
2 Drive e: (WinRE) (Fixed) (Total:1.46 GB) (Free:1.11 GB) NTFS
3 Drive f: (Repair disc Windows 7 64-bit) (CDROM) (Total:0.21 GB) (Free:0 GB) UDF
4 Drive g: (USB2) (Removable) (Total:3.72 GB) (Free:3.42 GB) FAT32
5 Drive x: (Boot) (Fixed) (Total:0.03 GB) (Free:0.03 GB) NTFS

  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
  Disk 0    Online          111 GB  3072 KB         
  Disk 1    Online         3814 MB      0 B         

Partitions of Disk 0:
===============

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Recovery          1500 MB  1024 KB
  Partition 2    Primary             55 GB  1501 MB
  Partition 3    Primary             54 GB    57 GB

==================================================================================

Disk: 0
Partition 1
Type  : 27
Hidden: Yes
Active: No

  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
* Volume 3     E   WinRE        NTFS   Partition   1500 MB  Healthy    Hidden  

==================================================================================

Disk: 0
Partition 2
Type  : 07
Hidden: No
Active: Yes

  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
* Volume 1     Y                RAW    Partition     55 GB  Healthy            

==================================================================================

Disk: 0
Partition 3
Type  : 07
Hidden: No
Active: No

  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
* Volume 2     D   Data         NTFS   Partition     54 GB  Healthy            

==================================================================================

Partitions of Disk 1:
===============

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Primary           3810 MB  4032 KB

==================================================================================

Disk: 1
Partition 1
Type  : 0C
Hidden: No
Active: Yes

  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
* Volume 4     G   USB2         FAT32  Removable   3810 MB  Healthy            

==================================================================================
==================== End Of Log =============================
```

---

### Post by MontyWest on 2012-09-24
Just to close this thread: MACHINE NOW WORKING 99%

Tried booting from a Vista Upgrade disc which was not able to repair the mbr.

After much searching, we found the original recovery disc issued with the laptop and rebooted. This reformatted the HD and re-installed Vista WITHOUT NEEDING THE PRODUCT KEY (the sticker was long gone from the underside of the machine).

I used Magical Jelly Bean finder to decrypt the product key and wrote it on a sticker in the battery bay for future use.

The machine has been thoroughly scanned for health and apart from the 72 reallocated sectors mentioned earlier has passed 100%. 

Thanks to everyone for input.

---

### Post by YannBuntu on 2012-09-25
Good job :)
Please use the Thread Tools to mark it [SOLVED].

---

