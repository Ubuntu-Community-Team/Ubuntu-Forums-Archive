---
title: "Linux Mint 14 installation issue."
date: 2012-11-30
forum: Any Other OS
---

### Post by Jizztasto on 2012-11-30
I apologize for the really lame question, but I just can't seem to be able to install it.
I've attempted installing it via USB and installing it via mint4win, neither of which worked.

I am stuck with the following and cannot proceed from here: [http://i.imgur.com/ylzVL.png](http://i.imgur.com/ylzVL.png)

If anyone can shed some light as to why this is occurring and how I can fix it I would be very grateful.
If it's not obvious; I'm quite new to *nix so once again, I apologize.

---

### Post by coffeecat on 2012-11-30
As this is about Linux Mint, *thread moved to **Other OS/Distro Talk**.*

However, I have a couple of suggestions. One common reason for seeing that installer window empty of partitions is using a hard drive that was once used in a RAID and the residual RAID metadata is confusing the installer. Was your hard drive once part of a RAID? If so, I can post a terminal command that will fix that.

The other possibility is a partition table irregularity which confuses the installer. Fairly easily fixed, but if your drive was not used in a RAID, lets see if this is so. Close the installer and open a terminal. Run this command and post the output:

```
sudo fdisk -lu
```

---

### Post by ajgreeny on 2012-11-30
From the live system desktop run the commands ```
sudo fdisk -l
``` and then ```
sudo parted -l
```I have suggested both as you may have GPT partitions and a UEFI bios.

---

### Post by Jizztasto on 2012-11-30
> **coffeecat said:**
> As this is about Linux Mint, *thread moved to **Other OS/Distro Talk**.*

However, I have a couple of suggestions. One common reason for seeing that installer window empty of partitions is using a hard drive that was once used in a RAID and the residual RAID metadata is confusing the installer. Was your hard drive once part of a RAID? If so, I can post a terminal command that will fix that.

The other possibility is a partition table irregularity which confuses the installer. Fairly easily fixed, but if your drive was not used in a RAID, lets see if this is so. Close the installer and open a terminal. Run this command and post the output:

```
sudo fdisk -lu
```

My apologies for posting it in the incorrect section.

I don't believe I've setup RAID, although I believe I have the ability to do so.

Here is the output, as requested:
```

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9083934c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    32940031    16429056    7  HPFS/NTFS/exFAT
/dev/sda3        32940032  3907018751  1937039360    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xba000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 4003 MB, 4003000320 bytes
32 heads, 63 sectors/track, 3878 cylinders, total 7818360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6960045b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     7818047     3908992+   c  W95 FAT32 (LBA)

```Thanks for the help so far!

---

### Post by coffeecat on 2012-11-30
Your fdisk output is showing that you have two hard drives: sda - 2TB and sdb - 32GB. (sdc is your flash drive.) Drive sda *appears* to have a mbr partition table and I can see no problem in the figures that would cause this problem. Drive sdb has no valid partition table.

ajgreeny's point about the possibility of GPT/UEFI is a good one, although I don't think the data you've posted so far says that you have, but let's be sure. A few more questions then.

[list][*]Let's have the output of "sudo parted -l" that ajgreeny suggested.
[*]What is your sdb - 32GB - drive? Something on that could still be confusing the installer.
[*]What model of computer are you trying to install to - I can see it's a Dell?
[*]What version of Windows do you have?
[*]Are you using the 32-bit or 64-bit Mint installer disk?[/list]

---

### Post by Jizztasto on 2012-11-30
> **coffeecat said:**
> Your fdisk output is showing that you have two hard drives: sda - 2TB and sdb - 32GB. (sdc is your flash drive.) Drive sda *appears* to have a mbr partition table and I can see no problem in the figures that would cause this problem. Drive sdb has no valid partition table.

ajgreeny's point about the possibility of GPT/UEFI is a good one, although I don't think the data you've posted so far says that you have, but let's be sure. A few more questions then.

[LIST]
[*]Let's have the output of "sudo parted -l" that ajgreeny suggested.
[*]What is your sdb - 32GB - drive? Something on that could still be confusing the installer.
[*]What model of computer are you trying to install to - I can see it's a Dell?
[*]What version of Windows do you have?
[*]Are you using the 32-bit or 64-bit Mint installer disk?
[/LIST]


Output of the command:
```

Model: ATA ST2000DM001-9YN1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary  fat16        diag
 2      41.9MB  16.9GB  16.8GB  primary  ntfs         boot
 3      16.9GB  2000GB  1984GB  primary  ntfs


Error: /dev/sdb: unrecognised disk label                                  

Model: FLASH Drive 3S_USB20 (scsi)
Disk /dev/sdc: 4003MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4003MB  4003MB  primary  fat32        boot, lba

```

I have no idea to be honest, it doesn't show up when I'm on Windows.
I can't mount the drive so I can't exactly tell you what's on there, sorry.

My model is called [XPS 8500]("http://www.dell.com/au/p/xps-8500/fs"), and I am running Windows 7 on it.
I've attempt both the 32-bit and 64-bit Mint installer, neither worked.
I am currently sticking with the 64-bit installer.

---

### Post by coffeecat on 2012-11-30
OK - you have a mbr partition table on sda, so you don't have a GPT/UEFI system. The 32-bit/64-bit question was in case you did have - the 32-bit installer doesn't work with UEFI. 

But now I'm puzzled. In your earlier post, fdisk showed your 2TB sda, a 32 GB sdb and your 4MB flash drive which is identified as sdc. But with the parted output, the 32GB drive has disappeared which is why the 4MB flash drive is now designated sdb.

We need to clarify what's going on with this 32GB drive before we can proceed. I have a feeling in my bones that the 32GB drive may be the problem. I know you say it doesn't show up in Windows, and that's because it doesn't have any partitions, not even a valid partition table. If you don't have any other information about what it could be, try rebooting into Windows and open Disk Manager - not Explorer - and see what that has to say about the hard drive(s) in your system.

---

### Post by Jizztasto on 2012-11-30
> **coffeecat said:**
> OK - you have a mbr partition table on sda, so you don't have a GPT/UEFI system. The 32-bit/64-bit question was in case you did have - the 32-bit installer doesn't work with UEFI. 

But now I'm puzzled. In your earlier post, fdisk showed your 2TB sda, a 32 GB sdb and your 4MB flash drive which is identified as sdc. But with the parted output, the 32GB drive has disappeared which is why the 4MB flash drive is now designated sdb.

We need to clarify what's going on with this 32GB drive before we can proceed. I have a feeling in my bones that the 32GB drive may be the problem. I know you say it doesn't show up in Windows, and that's because it doesn't have any partitions, not even a valid partition table. If you don't have any other information about what it could be, try rebooting into Windows and open Disk Manager - not Explorer - and see what that has to say about the hard drive(s) in your system.

You seem to be correct about the 32GB drive interfering with the installation.
I have the same machine at my other house, which is where I am now, so I can't continue to provide anything from the machine with the issue until sometime next week.

The installation seems to be working fine, with no problems.
I just executed mint4win and then proceeded with the reboot to find that I can proceed with the installation.
I would like to get it working on my other machine too, so I wish for this issue to be resolved.
Here's an image of it working, I'm unsure if this will help at all: [http://i.imgur.com/Fukgj.png](http://i.imgur.com/Fukgj.png)

I will also provide the output of the commands you gave me in your previous posts as it may or may not help you with resolving my issue.

**sudo fdisk -lu**
```

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa61ba3dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    32940031    16429056    7  HPFS/NTFS/exFAT
/dev/sda3        32940032  3907018751  1937039360    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xba000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 4003 MB, 4003000320 bytes
32 heads, 63 sectors/track, 3878 cylinders, total 7818360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6960045b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     7818047     3908992+   c  W95 FAT32 (LBA)

```**sudo parted -l**
```

Model: ATA ST2000DM001-9YN1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary  fat16        diag
 2      41.9MB  16.9GB  16.8GB  primary  ntfs         boot
 3      16.9GB  2000GB  1984GB  primary  ntfs


Error: /dev/sdb: unrecognised disk label                                  

Model: FLASH Drive 3S_USB20 (scsi)
Disk /dev/sdc: 4003MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4003MB  4003MB  primary  fat32        boot, lba

```**EDIT:** The issue seems to occur on this machine also, the drive that shows up in the installation is my thumb drive. It's not my actual hard drive.
I'm going to give up on installing Mint, it's just too frustrating. Thank you for the help anyway.

---

### Post by coffeecat on 2012-12-01
> **Jizztasto said:**
> I'm going to give up on installing Mint, it's just too frustrating. Thank you for the help anyway.

That's your choice and good luck. However, you appear to be giving inconsistent information which I am having difficulty following. Two machines? Are the data from two machines? 

I cannot see how the output from fdisk and parted in your latest post can be from the same machine at the same time. Again, the 32GB drive shows in the fdisk output but not in the parted output. Either these outputs are from different machines with different hardware configurations, or there is some feature of your Dell machine that is most unusual which needs investigating.

---

### Post by Jizztasto on 2012-12-01
> **coffeecat said:**
> That's your choice and good luck. However, you appear to be giving inconsistent information which I am having difficulty following. Two machines? Are the data from two machines? 

I cannot see how the output from fdisk and parted in your latest post can be from the same machine at the same time. Again, the 32GB drive shows in the fdisk output but not in the parted output. Either these outputs are from different machines with different hardware configurations, or there is some feature of your Dell machine that is most unusual which needs investigating.

The output is from two different machines, the machines are just the same model.
I attempted to install it on my other machine (*again, same model*) and it didn't work as you can see.

I did end up giving up on it and went to install Debian, embarrassed to say, I've screwed up my hard drive and now I can't seem to use it at all.
I followed [this]("https://www.youtube.com/watch?v=VpipA-_3nSs") step-by-step, and when it came to putting the files onto the partition I was given an error; something to do with the ext3 file system, I can't exactly recall it.
Anyway, I guess we won't be able to continue as my machine can't be fixed with my own knowledge. Luckily I've backed up all my files.
I can't even wipe it with a new install of Windows or Ubuntu, the drive just doesn't show up in the installers. It obviously doesn't recognize the drive due to partition being corrupted or something.
The nasty error: [http://digifixit.co.uk/tutorials/wp-content/uploads/2012/10/Reboot-and-Select-proper-Boot-device.jpg](http://digifixit.co.uk/tutorials/wp-content/uploads/2012/10/Reboot-and-Select-proper-Boot-device.jpg)

I'm going to ring Dell when possible and see if they're able to fix it.
Lesson: *nix obviously isn't for me. I can't seem to get anything working other than Ubuntu.
Quite ego shattering actually.

Well, thank you for trying to help me earler. x.x

---

### Post by coffeecat on 2012-12-01
I really think your issue could have been dealt with easily, but you complicated matters by posting the output of fdisk from one machine and then parted from the other. It doesn't matter that they are the same model - they clearly have different hardware configurations. Or are you saying the the first set of outputs from your posts #4 and #6 were from one machine and the outputs in post #8 are from the other? If so, I'm sure we could get to the bottom of this, but we need to know exactly what you are doing and where the outputs are from. I did have a suggestion, but was inhibited from posting it because of the discrepancy between fdisk and parted, and I am **still** not sure what you are doing.

A few specific comments:

> **Jizztasto said:**
> I did end up giving up on it and went to install Debian

I wouldn't advise installing Debian to beginners in Linux.

> **Jizztasto said:**
> 
I can't even wipe it with a new install of Windows or Ubuntu, the drive just doesn't show up in the installers. It obviously doesn't recognize the drive due to partition being corrupted or something.

The screenshot you posted is more-or-less what I would expect after your unsuccessful attempt with Debian. I really don't think this is likely to be a big issue. I'm sure it is easily fixed.

> **Jizztasto said:**
> I'm going to ring Dell when possible and see if they're able to fix it.

Hmmm - you have a wealth of experienced members on this forum.

> **Jizztasto said:**
> Lesson: *nix obviously isn't for me. I can't seem to get anything working other than Ubuntu.

Does that mean you have done a successful install of Ubuntu before? Mint uses the identical installer to Ubuntu. As I've said before, there are a number of possible issues we need to check with your hardware, and we haven't checked them all yet, to explain why the installer is failing.

If you do want help, **please settle on one and one machine only to work on.** There are a few things I would like to check that you can get from either the Mint or the Ubuntu live CD. If we can get you going with one machine, then we can turn our attention to the other, but only after getting the first sorted. If you want to start with the one that is now giving you the Reboot and Select Proper Boot Device error, that's fine.

---

### Post by Jizztasto on 2012-12-01
> **coffeecat said:**
> I really think your issue could have been dealt with easily, but you complicated matters by posting the output of fdisk from one machine and then parted from the other. It doesn't matter that they are the same model - they clearly have different hardware configurations. Or are you saying the the first set of outputs from your posts #4 and #6 were from one machine and the outputs in post #8 are from the other? If so, I'm sure we could get to the bottom of this, but we need to know exactly what you are doing and where the outputs are from. I did have a suggestion, but was inhibited from posting it because of the discrepancy between fdisk and parted, and I am **still** not sure what you are doing.


I apologize for the confusion, I didn't think switching machines would cause that much of a big deal because the same issue is occurring on both machines.
Yes, that is correct; post **#4** and **#6** are from the first machine, and post **#8** is from the second machine.

> 
I wouldn't advise installing Debian to beginners in Linux.

Really? I read it was a pretty easy installation and good for beginners.
Though, you seem to be well immersed in all of this, so I will take your word for it and steer away from Debian right and try and get this Linux Mint issue sorted.

> 
The screenshot you posted is more-or-less what I would expect after your  unsuccessful attempt with Debian. I really don't think this is likely  to be a big issue. I'm sure it is easily fixed.

I researched for hours and haven't been able to find a working solution.
Hopefully someone will see this and know what the problem may be.

> 
Does that mean you have done a successful install of Ubuntu before? Mint  uses the identical installer to Ubuntu. As I've said before, there are a  number of possible issues we need to check with your hardware, and we  haven't checked them all yet, to explain why the installer is failing.

Yes, although that was a different time and on a different machine.

> 
If you do want help, **please settle on one and one machine only to work on.**  There are a few things I would like to check that you can get from  either the Mint or the Ubuntu live CD. If we can get you going with one  machine, then we can turn our attention to the other, but only after  getting the first sorted. If you want to start with the one that is now  giving you the Reboot and Select Proper Boot Device error, that's fine.

The thing is I can't access the first machine until sometime next week and as you can see we can't try and get it working on the second machine due to my impatience and causing a boot error.
It would be faster to fix the boot issue and attempt Linux Mint again, although it's my own fault and I don't expect you to help me with it as it's a different issue to the Linux Mint.
If you don't mind the extra work, then I would be truly grateful.

I apologize for my impatience and ruining the progress we were making.
From now on I'll stick by it and see if we can get it working, without being hasty and doing stuff like that on my own.

Thank you again.

---

### Post by coffeecat on 2012-12-01
This is most interesting:

> **Jizztasto said:**
> 
Yes, that is correct; post **#4** and **#6** are from the first machine, and post **#8** is from the second machine.

Although fdisk and parted give slightly different information, which is why it was useful to have both outputs, they should not contradict each other. fdisk is telling us that you have three drives attached to the machine, sda - 2TB, sdb - 32GB and sdc - 4MB. By the way, neither fdisk nor parted distinguish between internal and external drives; the first internal physical drive would be sda, the second sdb, and so on, external drives being designated with drive letters from where the internal ones left off.  Whereas parted is saying that you have only the 2TB and 4MB drives - which us why your 4MB flash drive is appearing as sdc in fdisk and sdb in parted.

Frankly, I'm puzzled at the moment, and did not expect this.

Before we go any further, I'm going to pm another member to get a second opinion. He is in another time zone from me, so hang in there - you won't be forgotten! :)

---

### Post by oldfred on 2012-12-01
Is this a Intel SRT system. Those tend to be a large hard drive & small SSD to speed Windows up. Each vendor slightly different but the Intel part is the same.
Some delete the SRT and install Linux to the SSD, others turn off  SRT in Windows and have to use the RAID commands to remove RAID settings. Then after install they seem to be able to re-implement the SRT, but I do not then think Linux sees Windows.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

   You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by viper250 on 2012-12-02
from your display it is not detecting the drive partition table
there are a few things that can cause this

if your drives are sata drives make sure the data and power cables are connected properly ,
if they are ide drives make sure the jumpers are set correctly(usually set to cs(cable select))
and from the live menu select gparted
this should detect any hard drive that is connected unless the drive has crapped out.
if the drive shows up you can procede to rewrite the partition table and restart your installer.
have installed mint many times for others

if you want an easy linux to install try pinguyos 12.04. its a 7 step process in a graphical mode

---

### Post by Jizztasto on 2012-12-03
Apologies for the late reply!

I am quite happy right now, I've gotten past that nasty boot error and I am currently formatting my drive and putting Windows back on. :P
I can't exactly give a solution to the problem as I just kept trying random things and then it started working again.

I'm going to give Linux Mint another try once I've put all my files and whatnot back on my main machine.
I was so close to giving in and getting a new drive.

---

### Post by Jizztasto on 2012-12-04
The Linux Mint issue still persists, formatting didn't actually change anything (*not that I thought it would since it affects both machines.*)
I did watch a video on what's suppose to happen, still unsure why it doesn't show /dev/loop2 for me like it's suppose to.

---

### Post by robert shearer on 2012-12-04
From the o/p original post....

> I've attempted installing it via USB and installing it via mint4win, neither of which worked.

I am guessing the 'via USB' was still using **mint4win**
This is the Mint version of WUBI.

Is the phantom 32GB drive perhaps the amount you allocated as the mint4win install....?

---

### Post by Jizztasto on 2012-12-04
> **robert shearer said:**
> From the o/p original post....



I am guessing the 'via USB' was still using **mint4win**
This is the Mint version of WUBI.

Is the phantom 32GB drive perhaps the amount you allocated as the mint4win install....?

I also attempted mounting it via Daemon Tools, same outcome.
The 32GB drive was there after I formatted my drive, so I wouldn't say so.

---

### Post by coffeecat on 2012-12-04
> **robert shearer said:**
> 
Is the phantom 32GB drive perhaps the amount you allocated as the mint4win install....?

> **Jizztasto said:**
> 
The 32GB drive was there after I formatted my drive, so I wouldn't say so.

@Jizztasto, please see oldfred's post. The 32GB drive is almost certainly part of the Intel SRT system. I must admit, this one was new on me. The links that oldfred posted give more information. One thing to beware of is that you may still have the complication of Intel SRT interfering with the Ubuntu/Mint installer because of the RAID metadata. There are workarounds in oldfred's links.

---

### Post by Jizztasto on 2012-12-05
Hell yes! You guys were right!
It was to do with the RAID devices, all I had to do was remove the **dmraid** package from Linux. :P

```

sudo apt-get remove dmraid

```

Thanks a lot guys! Proceeding with the installation, wish me luck! :P

---

### Post by cypher_zero on 2013-02-18
Just wanted to comment here that I had the exact same problem (different machine) and the solution given here worked for me.

---

### Post by Alan_Schofield on 2013-09-09
In case anyone else stumbles across this... I had the a very issue with Mint 15. I was installing from CD though with no existing OS in place.
I was using a redundant HDD so, after my first failed install attempt, I use GParted to remove the existing partitions.
Thinking this would be enough (I guessed the installer would offer to create the partitions) I attempted to install again. Same issue, no HDD listed to install from.
So I created the partitions and tried again, still no luck.
Using GParted I fished around in the device info of the drive hoping to find something missing but no luck so I removed the partitions again. This time though, I didn't add the partitions but what I did do was to use the 'Create partition table' option on the drive menu, keeping the default msdos setting.
Looking at the drive info again didn't reveal any changes from when I started all this but I ran the installer and hey-presto! there was the drive just itching to be installed onto !

Anyway, It's looking good so far, just about to reboot though, so knowing my luck it's all go pear-shaped again!

---

