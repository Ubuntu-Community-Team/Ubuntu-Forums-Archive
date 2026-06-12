---
title: "Mounting HFS+ usb drives that have a GUID partition table"
date: 2008-11-23
forum: Apple Hardware Users
---

### Post by BurkDP on 2008-11-23
After reading this amazing article: HowTo: Make Ubuntu A Perfect Mac File Server And Time Machine Volume (http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/) and getting netatalk to work I can say it fraking screams - I can quicklook a high quality video file with no lag (even skip around!) so hooking a drobo (http://www.drobo.com/) up to a second computer and creating a file server is a no brainer.

My problem: I can't seem to get any usb drives I format with my mac to mount on an Ubuntu system. I can't just reformat, because I only recently got my drobo and I've already formatted with my MacBook - it simply has too much stuff to do that.
*I did read this post: http://ubuntuforums.org/showthread.php?p=2346494#post2346494 But it's about dealing with issues **after** a drive has mounted.

I did do a google/ubuntu forums search but I'll admit I didn't look past 2 pages into each search. I thought that it'd be easier to simply ask if someone knows how to fix this, so forgive me if this is an oft asked question with a repeated, glaringly obvious solution.


**Here's What I did**
Equipment Used (2 computers, 1 usb hard drive):
Ubuntu Computer - "Hardy Heron" kernel 2.6.24-19-generic, x86_64
MacBook 1,1 - Mac OS X v10.5.5
Freshly formatted USB 2.0 232.9GB WD drive, 1 HFS+ partition with a GUID Partition Table
*Formated using Disk Utility on my MacBook

Like I usually do to find out what to mount I type ```
sudo fdisk -l
```
*I get:
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       30402   244198583+  ee  EFI GPT

```

Undaunted, I try ```
mount /dev/sdg1  -t hfsplus ~/usb_drive
```
*I get:
```

danielburk@Hohenheim:~$ sudo mount /dev/sdg1  -t hfsplus ~/usb_drive
mount: wrong fs type, bad option, bad superblock on /dev/sdg1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

As prompted I try ```
dmesg
```
*I get:
```

[268196.288021] usb 6-5: new high speed USB device using ehci_hcd and address 5
[268196.424565] usb 6-5: configuration #1 chosen from 1 choice
[268196.451784] scsi6 : SCSI emulation for USB Mass Storage devices
[268196.464351] usb-storage: device found at 5
[268196.464360] usb-storage: waiting for device to settle before scanning
[268201.467359] usb-storage: device scan complete
[268201.468597] scsi 6:0:0:0: Direct-Access     WD       2500BEVExternal  1.02 PQ: 0 ANSI: 0
[268201.480837] sd 6:0:0:0: [sdg] 488397168 512-byte hardware sectors (250059 MB)
[268201.481939] sd 6:0:0:0: [sdg] Write Protect is off
[268201.481945] sd 6:0:0:0: [sdg] Mode Sense: 00 00 00 00
[268201.481947] sd 6:0:0:0: [sdg] Assuming drive cache: write through
[268201.484055] sd 6:0:0:0: [sdg] 488397168 512-byte hardware sectors (250059 MB)
[268201.485059] sd 6:0:0:0: [sdg] Write Protect is off
[268201.485064] sd 6:0:0:0: [sdg] Mode Sense: 00 00 00 00
[268201.485066] sd 6:0:0:0: [sdg] Assuming drive cache: write through
[268201.485112]  sdg: sdg1 sdg2
[268201.578256] sd 6:0:0:0: [sdg] Attached SCSI disk
[268201.578370] sd 6:0:0:0: Attached scsi generic sg6 type 0
[268278.893287] hfs: unable to find HFS+ superblock

```

I read this post: http://ubuntuforums.org/showthread.php?p=2346494#post2346494
*I get the feeling that it won't help much, as it assumes drives will mount in the first place.

I return to my mac, and plug hard drive in fire up terminal.app and type ```
diskutil list
```
*I get pertinant information about Hard Drive:
```

/dev/disk3
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *232.9 Gi   disk3
   1:                        EFI                         200.0 Mi   disk3s1
   2:                  Apple_HFS Untitled                232.6 Gi   disk3s2

```

I thought I'd see if the filesystem has a problem I can fix while I'm here. I try ```
diskutil repairVolume /Volumes/Untitled
```
*The drive has no errors:
```

sudo diskutil repairVolume /Volumes/Untitled/
Started verify/repair volume (filesystem) on disk disk3s2 Untitled
Checking Journaled HFS Plus volume
Checking Extents Overflow file
Checking Catalog file
Checking multi-linked files
Checking Catalog hierarchy
Checking Extended Attributes file
Checking volume bitmap
Checking volume information
The volume Untitled appears to be OK
[ + 0%..10%..20%..30%..40%..50%..60%..70%..80%..90%..100% ] 
Finished verify/repair volume (filesystem) on disk disk3s2 Untitled

```

---

### Post by BurkDP on 2008-11-23
It mounts just find under 8.10 gui. I can read/write to it as well. This is freaking annoying, it's like it's mocking me.

Here's the output from dmesg:
*Does this contain how it's doing it somewhere in here?
```
[  591.572124] usb 5-2: new high speed USB device using ehci_hcd and address 8
[  591.719209] usb 5-2: configuration #1 chosen from 1 choice
[  591.722223] scsi9 : SCSI emulation for USB Mass Storage devices
[  591.723253] usb-storage: device found at 8
[  591.723269] usb-storage: waiting for device to settle before scanning
[  596.720413] usb-storage: device scan complete
[  596.721136] scsi 9:0:0:0: Direct-Access     WD       2500BEVExternal  1.02 PQ: 0 ANSI: 0
[  596.725341] sd 9:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[  596.726097] sd 9:0:0:0: [sde] Write Protect is off
[  596.726105] sd 9:0:0:0: [sde] Mode Sense: 00 00 00 00
[  596.726112] sd 9:0:0:0: [sde] Assuming drive cache: write through
[  596.726838] sd 9:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[  596.727587] sd 9:0:0:0: [sde] Write Protect is off
[  596.727594] sd 9:0:0:0: [sde] Mode Sense: 00 00 00 00
[  596.727600] sd 9:0:0:0: [sde] Assuming drive cache: write through
[  596.727609]  sde: sde1 sde2
[  596.822367] sd 9:0:0:0: [sde] Attached SCSI disk
[  596.822553] sd 9:0:0:0: Attached scsi generic sg5 type 0
[  597.228009] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
```

---

### Post by cyberdork33 on 2008-11-23
fdisk can only read the mbr partition table. You tried to mount the EFI partition as hfs+, which doesn't work because that is the wrong fs type.

the hfs+ partition is partition 2 or sdg2...

parted can read the gpt. use it to view partitions on your hard drive, or use gparted.

---

### Post by jevchance on 2009-04-13
BurkDP, did you ever get a resolution to this? I'm having the exact same issue, and would appreciate any advice.

---

### Post by BurkDP on 2009-04-13
Yeah, it's really simple. It's like they said, you have to mount the second partition. Oh, and make a folder to mount it to in /mnt (if you don't have a gui it won't automatically do make one).

Here's a writeup of how I did it: [http://burk.crabula.com/index.php?title=New_Headless_Ubuntu_Server_Guide#Making_A_Mount-Point_For_Drobo_.26_Link_To_It_In_.24HOME](http://burk.crabula.com/index.php?title=New_Headless_Ubuntu_Server_Guide#Making_A_Mount-Point_For_Drobo_.26_Link_To_It_In_.24HOME)

Oh yeah, if you can't write to an HFS+ drive it probably has journaling enabled and you need to turn that off, which requires a Mac.

From a Mac open up the terminal.app (or iTerm, etc.) The volume name is whatever it's mounted as. I think if you just put a space after disableJournal and drag the drive icon into the terminal it's smart enough to put the path to it. You may have to use sudo.

*diskutil disableJournal [volumeNam]*


These are the programs that can read a GUID partition table. If you have a gui install **gparted**, otherwise install **parted**.

*sudo aptitude install [parted/gparted]*

Also if you can mount it, but not write it (with journaling disabled) it might need repairing - like how you can use disk utility to repair a drive. To do that from Ubuntu all you need to do is install **hfsprogs**.

*sudo aptitude install hfsprogs*

and to repair it:

[I]sudo umount [drive ex. /dev/sdf2]
sudo fsck.hfsplus /dev/sdf2
sudo mount /dev/sdf2 -t hfsplus -o rw /mnt/Drobo[/I]


One last thing - if you have Ubuntu on a mac check this out: [https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)
> Several savy Ubuntu Mac users have fixed bugs, and added functionality to certain software in order to make Ubuntu run better on certain Macs and placed them in a repository available to Ubuntu users until the fixes make it in to the main Ubuntu release.

---

