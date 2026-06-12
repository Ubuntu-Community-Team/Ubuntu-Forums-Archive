---
title: "Western Digital Does Not Support Linux"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by canadastitan on 2008-04-16
Hello..Help Please..!!
.. I Deleted my windows partition on my Western Digital 500 gig MYBOOK AND SET 3 NEW PARTITIONS 1= /dev/sdb1/ ..EXT2..463 GiB Primary ..2= /Ddev/sdb2/..1.36 GiB.Linux Swap ..3= /dev/sdb3/ ..1.36 GiB.extended
I had previously set label to msdos..
The problem is when i try to mount the external usb drive i get error message
(( Cannot mount volume) The volume uses the EXT3 file system which is not supported by your system)
..Which is very strange as I am running ubuntu 7.10 and my main hdd is the ext3 format ,but i set format on external hdd to ext2 using (sudo gparted)..I actually need the external to be EXT2..?? IS THIS A BUG IN UBUNTU..Or did I do something wrong..??
.........................................................................................................
I am running ubuntu 7.10 on Acer TravelMate 2303LCi,It has internal 40 gig hdd formated to ext3,trying to use 500 gig external Western Digital MyBook formatted to ext2

---

### Post by canadastitan on 2008-04-16
With the trouble that I have been having with my new Western Digital 500 gig MYBOOK ..I have contacted Western Digital about these problems and asked for a partioning Drive health utility for my new drive, Like the one they have for a Microsoft based computer called "Data Lifegaurd"..
And this is the response i received..!!
.............................................................................................................................................
 Dear XXXX,
> 
> Thank you for your reply.
> 
> I am sorry, but Western Digital does not provide Linux support for either our external or internal drive. I would also like to note that our Data Lifeguard tools software also does not work on a Mac system, and is only supported on a PC based computer.
> 
> Please let us know if we can be of further assistance.
> 
> Sincerely,
> Don S.
> Western Digital Service and Support
> [http://support.wdc.com](http://support.wdc.com)
.........................................................................................................................
I wonder why everyone who makes computers and sells them would install a hard drive that does not get any support from the builder of the hard drive...
..Does anyone Know of a brand of HDD  that come's with drive health support for Linux or Mac..??

---

### Post by Lolicon on 2008-04-16
My internal device works fine. Is it mounting correctly?

---

### Post by SunnyRabbiera on 2008-04-16
Seagate

---

### Post by itix on 2008-04-16
My red external Western Digital (pretty as hell) 120 gb works fine as long as I run gutsy, to which I'm going to change tomorrow morning since I'm sick and tired of all the bugs in hardy. How the hell is ubuntu's programmers going to solve the remaining problems in compiz, mount/nautilus/wherever it is that refuses me the right to write to my own external drive without root properties, the minor graphical errors here and there...

Back to gutsy it is, and there I'll stay until next month.

---

### Post by itix on 2008-04-16
Anyway, my point is; my external drive actually works. Are you sure that it's linux that is the problem? A hard drive is a hard drive and can as far as I know not be OS specific...

---

### Post by dasunst3r on 2008-04-16
It looks like what you need is a way to partition drives and check on its health.  For that, there's *gparted* and *smartmontools*.  You can install both of these through the repositories.  GParted is located in System -> Administration.  *smartmontools*, on the other hand, is used through the terminal.  Here's an example of its output:
```
dasunst3r@hastalavista2:~$ sudo smartctl -a /dev/sda
[sudo] password for dasunst3r: 
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio family
Device Model:     WDC WD800BEVS-75RST0
Serial Number:   [redacted]
Firmware Version: 04.01G04
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Apr 16 20:39:17 2008 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (3780) seconds.
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
recommended polling time: 	 (  51) minutes.
Conveyance self-test routine
recommended polling time: 	 (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   160   160   021    Pre-fail  Always       -       966
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2393
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       5313
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2382
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       430
193 Load_Cycle_Count        0x0032   184   184   000    Old_age   Always       -       48741
194 Temperature_Celsius     0x0022   107   088   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      3577         -
# 2  Short offline       Completed without error       00%         2         -
# 3  Short offline       Completed without error       00%         0         -

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

### Post by Jawshie on 2008-04-16
I always hate it when people say PC and really mean "Windows." When did PC become a term that automagically meant Windows? 

Anyways, sorry to hear about your drives not working. I don't have any problems with my WD drives but I may think to learn towards Seagate now. Thanks :)

---

### Post by Lolicon on 2008-04-16
Seagate isn't garbage, but I like WD more. My seagate always runs hotter than my WD even though I tried to like it. If you format it to ext3 it may run, but I think your problem is its not mounting correctly.

---

### Post by canadastitan on 2008-04-16
Yes I know my external is not mounting correctly..as i used gparted to partition it and set format to 3 devices 1= ext2... 2= linix swap.. 3= extended...works fine if i cross platform mount it with windows xp or a pvr..??
.But when i try to mount it on this laptop..it comes up with error message CANNOT MOUNT..
..::says its a ext3 file system which is not supported by my system""
..??which is weird as my other internal WD 40 gig is set to ext3..and running fine on my ubuntu os..!!
..I figgure its some kind of bug in ubuntu 7.10 and wanted help from western Digital to be able to check that external 500 gig out with a diagnostic utility..but got that shitty response that i felt offended by..as I AM RUNNING A PC WITH A NON MICROSOFT OPERATING SYSTEM..
..Abd they refer to and only seem to support Microsoft..What do they think Unix/Linux are if they do not consider these a pc based operating system..
Just tjhought you all should know..

---

### Post by canadastitan on 2008-04-16
> **dasunst3r said:**
> It looks like what you need is a way to partition drives and check on its health.  For that, there's *gparted* and *smartmontools*.  You can install both of these through the repositories.  GParted is located in System -> Administration.  *smartmontools*, on the other hand, is used through the terminal.  Here's an example of its output:
```
dasunst3r@hastalavista2:~$ sudo smartctl -a /dev/sda
[sudo] password for dasunst3r: 
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio family
Device Model:     WDC WD800BEVS-75RST0
Serial Number:   [redacted]
Firmware Version: 04.01G04
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Apr 16 20:39:17 2008 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (3780) seconds.
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
recommended polling time: 	 (  51) minutes.
Conveyance self-test routine
recommended polling time: 	 (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   160   160   021    Pre-fail  Always       -       966
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2393
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       5313
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2382
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       430
193 Load_Cycle_Count        0x0032   184   184   000    Old_age   Always       -       48741
194 Temperature_Celsius     0x0022   107   088   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      3577         -
# 2  Short offline       Completed without error       00%         2         -
# 3  Short offline       Completed without error       00%         0         -

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

Thanks I Will Give This A Try

---

### Post by wolfen69 on 2008-04-16
the new WD MyBook external drives will not work in linux without a workaround. do a google search for- western digital my book linux. you will see many people that are having major problems.

also, the seagate "free agent" hard drives will not work with linux.

---

### Post by aktiwers on 2008-04-17
Sounds very odd! 
Did you try run fsck on the disk?

First unmount it and then:
```
sudo fsck -ry /dev/sdb1
```
then
```
sudo fsck -ry /dev/sdb2
```
then(well don't think it works on swap drives?)
```
sudo fsck -ry /dev/sdb3
```

---

### Post by canadastitan on 2008-04-17
when i try "sudo gparted"     i get both drives
-----------------------------------------------------------------------------------------------------------------------------------
_/dev/sda      37.26 GiB_  (my internal 40 gig with ubuntu 7.10 installed on it)

                                    Mount Point     Size               Used               Unused         Flag
/dev/sda1      ext3                  /           35.87 GiB           3.01 GiB          32.85 GiB    Boot
/dev/sda2      extebded                         1.39 GiB          ....                    ....
/dev/sda3      LinuxSwap                       1.39 GiB          ....                    ....   
------------------------------------------------------------------------------------------------------------------------------------
_/dev/sdb    456.76 GiB_   (my external 500 gig WD MyBook )

                                    Mount Point     Size               Used               Unused         Flag
/dev/sdb2      LinuxSwap                       4.88 GiB          ....                    ....
/dev/sdb1      ext2                             460.88 GiB       18.69 GiB       442.19 GiB          
-----------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------
when i try "sudo fsck -ry /dev/sdb1"        this is what i get
-----------------------------------------------------------------------------------------------------------------------------
canadastitan@acer:~$ sudo fsck -ry /dev/sdb1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb1: clean, 35/60424192 files, 4898938/120816832 blocks
canadastitan@acer:~$ 
-----------------------------------------------------------------------------------------------------------------------------
and then "sudo fsck -ry /dev/sdb2"
-----------------------------------------------------------------------------------------------------------------------------
canadastitan@acer:~$ sudo fsck -ry /dev/sdb2
fsck 1.40.2 (12-Jul-2007)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sdb2
canadastitan@acer:~$
-----------------------------------------------------------------------------------------------------------------------------
If I Try to Mount the External Drive /dev/sdb,either by cold booting system or hot mounting it or trying to mount it with ubuntu
__ "I always get error message"__

                                    Cannot mount volume
      The volume uses the EXT3 file system which is not supported by your system.
-----------------------------------------------------------------------------------------------------------------------------
I find this very strange as my /dev/sda is ext3 and works fine
But i can never mount my external ext2 drive..??
-------------------------------------------------------------------------------------------------------------------------------
Is this maybe a bug in the ubuntu 7.10 software..???

---

### Post by northern lights on 2008-04-17
This sounds quite wicked. I'm thinking about it - dumbfounded so far.

Anyways - the reason for posting is that, on a side note, you should not run "gparted" with "sudo". Actually you should never run any graphical app with "sudo". Most often it will work, but can screw you over when it comes to permissions. Run ```
gksu gparted

or

gksu <graphical app>
```
instead.

---

### Post by aktiwers on 2008-04-17
have you tried force mount it?

Also have a look here:
[http://tldp.org/HOWTO/Filesystems-HOWTO-6.html](http://tldp.org/HOWTO/Filesystems-HOWTO-6.html)

---

### Post by itix on 2008-04-17
I have a USB stick that OFFICIALLY support linux. I just found a penguin at the sticker on the back and read through the manual :)

---

### Post by canadastitan on 2008-04-17
I am not sure how to force mount it..??
will try deleting the drive and partitioning it again using gksu gparted..
and set main partition to ext3 and see if it helps..
I have tried the hdd on a PVR and also on a windows xp pro,running extfr and it works fine..
which is why i am puzzeled that if ubuntu created the ext file system ..why doesnt it let me mount it..??
oh yes i read that link about how to filesystems..and still are foggy about what purpose the Linux Swap and the extended partitions do on my hard drives..

---

### Post by misfitpierce on 2008-04-18
Why not just reformat the drive FAT32/FAT like it comes default. I have my 500GB still FAT formatted and it gives me no problems.

---

### Post by canadastitan on 2008-04-18
fat 32 does not support large file systems properly ..!!
,,And i use my 500 gig on my VS 9000 HD PVR also can  hot mount it to a windows xp computer to rename the file folder names..(which is the recorded program name)..and I should be able to mount it to my ubuntu linux computer but it gives error cannot mount..!! ..Which is strange as the filesystem was created with the ubuntu linux laptop..??

---

### Post by canadastitan on 2008-04-18
i do not have smartctl installed ..??i tried sudo apt-get install smartctl
..could not find it..??

---

### Post by misfitpierce on 2008-04-18
So you got to make 2 threads about your MyBook? Please constrain it to 1 thread rather than spamming boards with multiple threads on your MyBook and that would be greatly appreciated :) Thanks.

---

### Post by canadastitan on 2008-04-19
this is what happend 
canadastitan@acer:~$ sudo smartctl -a /dev/sdb1
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: WD       5000AA External  Version: 200i
Device type: disk
Local Time is: Sat Apr 19 00:09:55 2008 CDT
Device does not support SMART

Error Counter logging not supported
Device does not support Self Test logging
canadastitan@acer:~$

---

### Post by canadastitan on 2008-04-21
I am starting to think that this strange problem has something to do with western digital 500 gig mybook loosing its smart controll..ALONG WITH THE NON SUPPORT FROM THE MANUFACTURER ..So I guess I am gonna toss it to my kids to use on their game system and look for a external hdd that works correctly in the unix/linux ext2/3 format..I WILL NEVER BUY A WESTERN DIGITAL HDD AGAIN (NOR WILL I BUY A COMPUTER WITH WESTERN DIGITAL DRIVES IN IT)
??.((WHAT BRANDS WORK WITH LINUX)(and come with drive health software for unix/linux))??

---

### Post by joshrobinson on 2008-04-21
weird, i have 2 WD hard-drives in my fileserver, and they work perfect
also a maxtor that works great

> **Jawshie said:**
> I always hate it when people say PC and really mean "Windows." When did PC become a term that automagically meant Windows? 

Anyways, sorry to hear about your drives not working. I don't have any problems with my WD drives but I may think to learn towards Seagate now. Thanks :)

this drives me nuts also, especially those PCvsMac comercials that dont mention windows (the newer ones mention vista and xp)
i own PC's, but no windows machines, and my PC is more secure then a mac

---

### Post by canadastitan on 2008-04-27
Ok it definatly was the WD 500 gig mybook that was the problem..
I removed it as its smart was bad and the fact Western Digital stated to me they DO NOT SUPPORT LINUX..
..So i went and bought a TREKSTOR 500 gig HDD at FutureShop and It works correctly with ubuntu linux..I have no more problems..!!
The TREKSTOR COMES WITH A LITTLE PENGUIN ON THE BOX SHOWING THAT IT SUPPORTS LINUX..
..It comes in vfat(fat32) format with mount point /media/TREKSTOR/ and works fine right out of the box

---

