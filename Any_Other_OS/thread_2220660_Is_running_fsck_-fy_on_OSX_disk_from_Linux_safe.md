---
title: "Is running fsck -fy on OSX disk from Linux safe?"
date: 2014-04-28
forum: Any Other OS
---

### Post by GameX2 on 2014-04-28
Hi,


I have a problem with the MacBook Pro of a friend;
OS X would completely fail to boot - we've tried different stuff, all unsuccesful including:

-Reset NRAM/PRAM;
-Boot into Safe Mode
-Boot into command-line / Single-User mode, which display something like this (don't remember the exact line, will check again: hfs_mountroot failed: 5 cannot mount root, errno = 19.  Can't mount root?);
-I also got a "No-Way" sign (Does this mean, basically hard-drive not found?), and even a Kernel Panic.
-Boot from recovery partition and verify disk; oddly, the disk is not even seen by OS X at all, so I can't verify it!  Nor in the terminal.  Should I list the partitions and try to mount it manually?

It may sound like a dead hard-drive, but still, I did managed to boot on my Ubuntu 13.04 x64 USB drive and access the OS X partition.  I accessed all the files, and apparently managed to backup everything, at least in the Users folder.  I should note that the drive takes at least 2 minutes to simply show up in Nautilus.  And Ubuntu was really glitchy, lots of graphics glitchs and even prone to instant crash when moving the mouse for too long.  I don't worry about that much, because I run it on Apple hardware without any tweaks to make it more compatible, but still.

I can't understand much why OS X can't see the drive AT ALL (?!?), while I did accessed the hard drive in Ubuntu and copied everything, without possibly any "apparent" sign of corruption.  Is this exclusively a OS X boot problem, a single partition?

Of course, it's an Ubuntu forum, not an OS X, but I would appreciate at least one advice:
Next, I will try the boot disk "DiskWarrior" and see what will happen.  Additionally, I guess I could use fsck -fy from Linux to check the drive (Seems like OS X has the same command built-in his Disk Utility, so).  I am aware that I will need to unmount the partition first to avoid damage.  But running it from Ubuntu to an OS X partition (HFS+), is this safe, even if it's the same command?

Is is required to install  hfsprogs before fsck (To write on HFS+ drives)?  Since I have no Wifi, will try to install it from a Raring DEB, please correct me if I need to do something else; 
Also, should disabling journaling be done before the fsck command?  How long should the command last (My guess, from 30 minutes to 389 years) ?

EDIT: I also have to try testdisk - used it in the past with lot of success. [http://perrohunter.com/repair-a-mac-os-x-hfs-partition-table/](http://perrohunter.com/repair-a-mac-os-x-hfs-partition-table/)

If you have anything else in mind I could try to fix the boot issue, please let me know, I appreciate it.

---

### Post by jasonvp on 2014-04-29
> **GameX2 said:**
> 
Additionally, I guess I could use fsck -fy from Linux to check the drive (Seems like OS X has the same command built-in his Disk Utility, so).  I am aware that I will need to unmount the partition first to avoid damage.  But running it from Ubuntu to an OS X partition (HFS+), is this safe, even if it's the same command?

No good is going to come from running Linux's fsck on a BSD-style filesystem.  Remember that the first two letters of fsck, fs, mean *file system*.  Not disk.  Berserkley's journaled filesystem isn't the same as ext[3,4], and the latter are what Linux's fsck is written to handle.

There's something about that disk that the Mac's EFI doesn't like, for some reason.  Since you have the data that you need from it, it may be worth nuking it from orbit to see if you can continue using it.  But, I wouldn't hold my breath.  I assume you have a bootable USB OS X installer?  (If you don't: why not?!)  Boot with that, go into the Disk Utility, and see if it recognizes the drive on your Mac.  Assuming it does, format it first.  Then tell the OS X installer to use it.  Get some popcorn, sit back, and wait.

If Disk Utility doesn't recognize it, then I'm afraid that disk has had it from a Mac perspective.  Either attach it to a PC and use it there, or drop it in a chipper/shredder and dispose of it.

---

### Post by bapoumba on 2014-04-29
Moved to Other OS Chat.

Depending on the MacOS version that is on the MacBook, you may want to try cmd-r when powering on the computer, hold it for long enough, this should boot you in the recovery partition where you can use Disk Utility.

If on a pre-Lion release, you should have install disks.

[http://support.apple.com/kb/ht4718](http://support.apple.com/kb/ht4718)

---

### Post by GameX2 on 2014-04-29
Thank you for replying;

EDIT3: This is the first time I try to fix a Mac, so I don't have OS X on a USB drive. :P I will try to find one, would appreciate if you know on top of your head where there is one.  I have the Snow Leopard installation CD, but not USB on me - I don't think there's a possibility to run OS X live from USB without install, but correct me if I'm wrong, I don't have much experience with Mac systems.

Although it's not my Mac (I don't own a Mac, but managed to run Mountain Lion with VMware, running well), I can confirm it's Snow Leopard and that we have the installation DVD - I am also aware that Snow Leopard is unsupported since February, will try to upgrade it / install Lion, the PC is a Intel Core 2 Duo, so should work. :/

I tried Cmd-R, booting from the Recovery Disk, and the OS X disk just isn't detected - doesn't appear on the list, so I can't verify it.  Use the Terminal as well, but I can't browse to the partition neither, like it wasn't mounted (But in the case, the drive wouldn't show up at all).

Lead me to think that the partition or boot sector got problem, I successfully mounted it on Linux (After 2 minutes of detection, is that a failure sign?) and backed up everything.  There could also be major problems with the drive, not just the partition :/

I will come back to you with the error message that appears when I boot Single-User mode.
Thanks

EDIT: Yes, when I boot in Single-User Mode, that's the message I get:

```

BRCM tunables:
pullmode[1] txringsize[ 256] txsendqsize[1024] reapmin[  32] reapcount[  128]

```

Freeze at this point...  Then this message show up every minute or so (Along with the No-Way sign):
```

Still waiting for root device

```

Which seems really logical that OS X cannot mount / , and would also explain that Ubuntu took 2 minutes to display the OS X drive in Nautilus.

EDIT: This look interesting, but this is for an Hackintosh: <bip bip was here>

---

### Post by jasonvp on 2014-04-29
> **GameX2 said:**
> I have the Snow Leopard installation CD, but not USB on me

If this Mac has a DVD drive, then you have all you need.  Pop the DVD in, hold the **C** key while the Mac is booting, and it should boot off of the DVD.  Follow the previous instructions from there, but don't expect much.

---

### Post by tgalati4 on 2014-04-29
What is the SMART status of this drive?  If you can boot Ubuntu, then you should be able to read the SMART status:

```
sudo smartctl -a /dev/sda
```

Otherwise I would stick to Disk Warrior or the native Mac Disk Utility (which can be run from a Live session from an OS X installer DVD).

If the SMART status shows lots of sector errors, then I would presume you have a physical/mechanical problem with the drive.  Pull it out, put it in a USB enclosure and pull a second copy of important files.  Also, spend some time to verify the integrity of user files that you have already backed up.  It's possible that you have a bunch of corrupted files.  If that is the case, then that would also indicate a failing drive.

How old is the disk?  How many power-on hours?  If more than 3 years or 10,000 hours, then you probaby need a new drive anyway.  No Apple Care means that machine no longer exists in the Mac ecosystem.

---

### Post by bapoumba on 2014-04-29
Please be aware that we wont support hackintosh or running MacOS X in a VM on non Apple hardware as this is breaking their Licence (I know that is not what you are doing here, as you have a MacBook with the adequate install disks).

Insert the disk and start up the MacBook holding down c, this should boot you into the installer. Make sure you have saved everything that was to be saved prior to doing this, because it will erase the HD and reinstall Snow Leopard.
[http://support.apple.com/kb/HT3910?viewlocale=en_US](http://support.apple.com/kb/HT3910?viewlocale=en_US)

If the HD is borked, that wont work, but then you'll know the HD is dead.

Edit, sorry, did not see tgalati4's post before replying. Please follow their recommendations before mine, as my suggestions are a one way drive (so to speak ;))

---

### Post by GameX2 on 2014-04-29
Allright, here's what I did;

Tried rebooting again with the Snow Leopard DVD, but still 

What I did noticed, is that pressing the Option key list all the drives, and 1 time out of like 5, the OS X drive isn't listed, just the USB drive.  In that case, if I choose to boot in Ubuntu, while the OS X drive did not appeared on boot, Ubuntu won't be able to find the disk at all, like it didn't existed, same for GParted.
However, I restarted a few times, pressed the Option key, and then the OS X drive showed up (As well as "Recovery 10.6").  Instead of choosing the OS X drive (Which would lead in a No-Way sign), I booted in Ubuntu, and the OS X partition was instantly found and accessible.  That way, I managed to take a screenshot of the partition layout:

[https://dl.dropboxusercontent.com/u/67605655/Screenshot%20from%202014-04-29%2019_36_17.png](https://dl.dropboxusercontent.com/u/67605655/Screenshot%20from%202014-04-29%2019_36_17.png)

Later ran smartctl (Had to install smartmontools from a Raring DEB because the MacBook was not connected to the Internet):

Had to enable SMART because it was not enabled:

```
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.8.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.
```

Then ran sudo smartctl -a /dev/sdc :

```
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.8.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA MK2555GSXF
Serial Number:    804NT5NZT
LU WWN Device Id: 5 000039 2b1b00c99
Firmware Version: FH405B
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Apr 29 19:51:02 2014 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  120) seconds.
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
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  87) minutes.
SCT capabilities:            (0x0039)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1034
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       10543
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       3668
 10 Spin_Retry_Count        0x0033   253   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       7020
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       922
192 Power-Off_Retract_Count 0x0032   096   096   000    Old_age   Always       -       2479
193 Load_Cycle_Count        0x0032   061   061   000    Old_age   Always       -       390682
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       36 (Min/Max 11/47)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       66
222 Loaded_Hours            0x0032   095   095   000    Old_age   Always       -       2304
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       251
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       2285

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

Huh, according to the output, test was passed.  I don't know, is that something wrong with /dev/sdc1 partition with the flag Boot, that would prevent OS X from booting, even when the harddrive is detected on startup?  I'm afraid the only reason why the drive show up 1 time out of 5 is a hardware failure.
As for when the MacBook was purchased, I don't know myself, will ask that tomorrow.  Almost sure it's at least 2-3 years old.  It's an Intel Core 2 Duo, 4GB of RAM with Snow Leopard, so (2009, maybe?).

Also tried holding Option on boot, then noticed the OS X disk (As well as Recovery) was detected.  I chose to boot with the Snow Leopard DVD, the Apple logo appeared, and after a while, the loading icon stop spinning.  The hard drive stop, freeze, nothing.  The DVD won't boot when the OS X partition is found on boot.  I rebooted again, noticed this time the OS X partition was not listed in the bootloader, chose the Snow Leopard DVD, and then it succesfully booted in the DVD.  That's weird because the DVD only boot when the OS X partition is not detected (?!?).

Thank you for the help, I appreciate it.

---

### Post by tgalati4 on 2014-04-29
The power-on hours are not excessive.  The load-cycle count (at 390,000) is rather high.  I have read that disks tend to wear out at 600K to 1.2 Million load cycles.  It's possible that a ribbon cable is loose.  Laptops tend to move around and a loose cable will cause similar symptoms.  Try reseating the disk cable at both ends.  It's also possible that the drive controller on the disk itself is going bad or the SATA controller on the motherboard is going bad.  The fact that multiple power cycles will cause the drive to show up is consistent with a failing chipset.

Check the corners of the laptop for drop damage.  One drop can loosen internal connections.

Because SMART was not enabled, no previous errors were captured, so you don't have a history of sector errors or relocation.  Because you can see the files in Ubuntu makes me think that the directory tree is intact and therefore a disk controller or disk power circuitry is failing.

Check the serial number of the macbook and see if it still has Apple Care.  If so, then make another data backup (verifying the files) and take it to the Genius Bar.  The Pro machines tend to get better service.

---

### Post by bapoumba on 2014-04-29
I'm not sure how much free space you need to be able to boot snow leopard (looked around but did not find the exact answer). Your pic shows the drive is almost full.

---

### Post by GameX2 on 2014-04-29
Wow, that's a really interesting tool, I should try this on my own hard-drive (Windows-Linux).  Thanks for all the infos.

Actually, the corners of the laptop *did* had a small bump (Don't know how you would tell it in English, well, corner is imperfect).  Unfortunately I won't have access to the MacBook until friday, but I can ask the owner to send a picture of it.
That possibility of a loose connection is also really well-thought, thank you.

Will get back to you on this.  And will try to free space from Ubuntu.

---

### Post by GameX2 on 2014-05-05
Almost sure I've found the problem, thanks to the theory you've provided me.  Although I haven't opened the MacBook, did more ressearch and found multiple users that said their MacBook Pro (2009 mostly) would display the exact same problem as this one, a folder with a question mark on boot.  When using another hard-drive, the problem would not be fixed, and when connecting the hard-drive as external on another computer, it did worked.

I assume it is the SATA cable, that connect the hard-drive to the motherboard.  There have been many, many users reporting problem about it, because this cable tend to wear out.

Links:

[https://discussions.apple.com/message/19330077#19330077](https://discussions.apple.com/message/19330077#19330077)

> 
**[Hard drive is not showing up in disk utility]("https://discussions.apple.com/message/19329640#19329640")**

I just took it to the apple store and they fixed it in less than ten  minutes. All that was wrong was that the cable that connects the hard  drive to the computer stopped working. The Mac genius simply replaced  the cable with a new one and that was that. My computer booted up and I  saw my old desktop wallpaper again and all my old folders. As if nothing  ever happened.  
The  total cost for the repair was $60 and my computer has been working  great ever since. Just take your Mac to your local apple store and  they'll fix it fast. 
 
I  should've just taken it the day it stopped working but instead I  panicked and bought a new hard drive. All that was unnecessary. 



[https://discussions.apple.com/thread/4434661](https://discussions.apple.com/thread/4434661)

> 
**[Broken SATA cable or logic board?]("https://discussions.apple.com/message/20025665#20025665")**


Today, this new SSD didn't show up in disk utilities, although it shows up on another laptop (booting into linux dvd). 
I've  placed the new SSD in the maindrive of my MacBook Pro 13" early 2011,  and i've placed my old HDD in an obtibay in the superdrive's place. The  HDD works fine, and i've installed the system onto there, since i can't  use my SSD. 
 
Could  this be a dead SSD (remember, it showed in Linux), a dead SATA-cable  (which i could fix), or a dead logic board connector (which i don't have  the balls to fix)? 

***

It was probably the cable going bad. This is a known weak link in all  MBPs. Some very funny things can happen when that cable starts to go.




[http://www.ifixit.com/Answers/View/112842/Is+my+hard+drive+cable+broken](http://www.ifixit.com/Answers/View/112842/Is+my+hard+drive+cable+broken)

> 
**[SIZE=4]Is my hard drive cable broken?[/SIZE]**

this afternoon, a few hours ago I got my cable SATA for MacBook Pro with  i5 processor, anyway. I installed it and finally was able to recognize  my new SSD, and even recognized my previous HDD which was not damaged  but the cable did not work. I can tell, the cable is the problem. It has  gone through many macbook pro early 2011; your macbook is the same  model as mine, maybe my solution is your solution! Good luck, and tell me!  Greetings from Veracruz, Mexico.


[http://forums.macrumors.com/archive/index.php/t-1170942.html](http://forums.macrumors.com/archive/index.php/t-1170942.html)

> 
My MBP cannot find the internal hdd. At first when I tried booting, the  famous "flashing folder with questionmark" appeared. After reading up a  bit, I found out that this means the MBP cannot find any OS to load. I  booted via the installation CD and tried reinstall the OS but failed as  it couldn't find any harddrive to install to. On the apple guide that I  was following it said that the most likely reason is that the harddrive  is broken(and thus losing all of my data on it) and must be replaced. I  was devastated! Lol.

***

Replacing the SATA cable is dead easy.  You can follow ifixit's guide  HERE.  ([http://www.ifixit.com/Guide/Repair/Installing-MacBook-Pro-13-Inch-Unibody-Mid-2009-Hard-Drive-Cable/1340/1](http://www.ifixit.com/Guide/Repair/Installing-MacBook-Pro-13-Inch-Unibody-Mid-2009-Hard-Drive-Cable/1340/1))   You can also buy the cable from them too, right HERE.  ([http://www.ifixit.com/MacBook-Parts/MacBook-Pro-13-Inch-Unibody-Mid-2009-Mid-2010-Hard-Drive-Cable/IF163-013?utm_source=ifixit_cart&utm_medium=cart_product_link&utm_content=product_list](http://www.ifixit.com/MacBook-Parts/MacBook-Pro-13-Inch-Unibody-Mid-2009-Mid-2010-Hard-Drive-Cable/IF163-013?utm_source=ifixit_cart&utm_medium=cart_product_link&utm_content=product_list))

Here's your problem summed up in one line:  known good hard drive is not recognized inside the machine.

Possible solutions:  replace HD cable or replace logic board.
It's far far far more likely to be the cable.  It's theoretically  possible that it could be the logic board, but it's insanely more likely  to be the cable.  On some MBPs, it's routed underneath the optical  drive, but on most machines, it's a five minute repair.


So we should be able to buy the cable off Amazon or eBay (Cheaper, but possibly less quality) - should be around 60$ if Apple does it, they fix it apparently in 10 minutes.
I really doubt the Mac owner is comfortable with doing the fix himself.

Instructions on how to replace it: [http://www.ifixit.com/Guide/MacBook+Pro+13-Inch+Unibody+Mid+2009+Hard+Drive+Cable+Replacement/1340](http://www.ifixit.com/Guide/MacBook+Pro+13-Inch+Unibody+Mid+2009+Hard+Drive+Cable+Replacement/1340)
Video: [http://www.youtube.com/watch?v=QSWQ-Vmumjk](http://www.youtube.com/watch?v=QSWQ-Vmumjk)

I will communicate the problem to him, and will get back to you on this.
Thank you for pointing me to the solution. =)

---

