---
title: "Triple boot Macbook Pro (Snow Leopard, Win7, Ubuntu)"
date: 2012-01-16
forum: Apple Hardware Users
---

### Post by ozxto on 2012-01-16
Hello ubuntu forums, I've gone through the process of creating a triple-boot system on my Macbook pro 6,2 (mid 2010) with OSX 10.6.8, Windows 7, and Ubuntu 11.10.  I have installed rEFIt, partitioned my drive appropriately, and installed Windows 7 successfully.  Ubuntu installed as well (I put grub in disk0s4), and I got to the part of restarting into Ubuntu when I read that the partition tables needed to be synced.  I booted back into rEFIt, went into the Partition tool, and got "analysis inconclusive" in response.

GPT partition table:  
diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            345.8 GB   disk0s2
   3:       Microsoft Basic Data BOOTCAMP                100.0 GB   disk0s3
   4:       Microsoft Basic Data                         50.0 GB    disk0s4
   5:                 Linux Swap                         4.0 GB     disk0s5

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       675729735   322.0 GiB   AF00  Customer
   3       675993600       871303167   93.1 GiB    0700  Untitled
   4       871303168       968957951   46.6 GiB    0700  Untitled
   5       968957952       976773119   3.7 GiB     8200  Untitled


MBR partition table:

sudo fdisk /dev/disk0
Disk: /dev/disk0	geometry: 60801/255/63 [976773168 sectors]
Signature: 0xAA55
         Starting       Ending
 #: id  cyl  hd sec -  cyl  hd sec [     start -       size]
------------------------------------------------------------------------
 1: EE 1023 254  63 - 1023 254  63 [         1 -         39] <Unknown ID>
 2: 0B 1023 254  63 - 1023 254  63 [        40 -     409600] Win95 FAT-32
*3: AF 1023 254  63 - 1023 254  63 [    409640 -  675320096] HFS+        
 4: 07 1023 254  63 - 1023 254  63 [ 675993600 -  195309568] HPFS/QNX/AUX


So it looks like the Ubuntu installation messed up my MBR partition table.  How do I go about fixing this?  Booting into OSX still works, but I haven't tried booting into Ubuntu, as I've read it'll just stay in a permanent hang.  I've read other threads having to do with this problem, but they're not all running with the same conditions I am.

Thanks in advance!

EDIT:  Let me know if there's any information I've left out that I need to include.

---

### Post by scognito on 2012-01-17
You should rewrite the MBR using gdisk on OSX.

Boot OSX
Download and install gdisk ([http://sourceforge.net/projects/gptfdisk/](http://sourceforge.net/projects/gptfdisk/))
sudo gdisk /dev/disk0
do a backup of GPT from there (press ? for help, I don't remember the entry)

Then edit your Hybrid MBR going to:
advanced tools (p)
edit Hybrid MBR (h)
Select your GPT partitions that you want on your MBR (you can select max 3), in your case just type "2 3 4" without quotes
Partition types are: AF for partition 2, 07 for other 2 (even if one has Linux)
Add protected "something" for first partition (used for grub): Y
Write (w)

Reboot, you should have your Linux bootable. Don't resync using refit if it is working!

Can't be more precise as I'm at work and don't have access to my mac.

Cheers

> **ozxto said:**
> Hello ubuntu forums, I've gone through the process of creating a triple-boot system on my Macbook pro 6,2 (mid 2010) with OSX 10.6.8, Windows 7, and Ubuntu 11.10.  I have installed rEFIt, partitioned my drive appropriately, and installed Windows 7 successfully.  Ubuntu installed as well (I put grub in disk0s4), and I got to the part of restarting into Ubuntu when I read that the partition tables needed to be synced.  I booted back into rEFIt, went into the Partition tool, and got "analysis inconclusive" in response.

GPT partition table:  
diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            345.8 GB   disk0s2
   3:       Microsoft Basic Data BOOTCAMP                100.0 GB   disk0s3
   4:       Microsoft Basic Data                         50.0 GB    disk0s4
   5:                 Linux Swap                         4.0 GB     disk0s5

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       675729735   322.0 GiB   AF00  Customer
   3       675993600       871303167   93.1 GiB    0700  Untitled
   4       871303168       968957951   46.6 GiB    0700  Untitled
   5       968957952       976773119   3.7 GiB     8200  Untitled


MBR partition table:

sudo fdisk /dev/disk0
Disk: /dev/disk0	geometry: 60801/255/63 [976773168 sectors]
Signature: 0xAA55
         Starting       Ending
 #: id  cyl  hd sec -  cyl  hd sec [     start -       size]
------------------------------------------------------------------------
 1: EE 1023 254  63 - 1023 254  63 [         1 -         39] <Unknown ID>
 2: 0B 1023 254  63 - 1023 254  63 [        40 -     409600] Win95 FAT-32
*3: AF 1023 254  63 - 1023 254  63 [    409640 -  675320096] HFS+        
 4: 07 1023 254  63 - 1023 254  63 [ 675993600 -  195309568] HPFS/QNX/AUX


So it looks like the Ubuntu installation messed up my MBR partition table.  How do I go about fixing this?  Booting into OSX still works, but I haven't tried booting into Ubuntu, as I've read it'll just stay in a permanent hang.  I've read other threads having to do with this problem, but they're not all running with the same conditions I am.

Thanks in advance!

EDIT:  Let me know if there's any information I've left out that I need to include.

---

### Post by ozxto on 2012-01-17
> **scognito said:**
> You should rewrite the MBR using gdisk on OSX.

Boot OSX
Download and install gdisk ([http://sourceforge.net/projects/gptfdisk/](http://sourceforge.net/projects/gptfdisk/))
sudo gdisk /dev/disk0
do a backup of GPT from there (press ? for help, I don't remember the entry)

Then edit your Hybrid MBR going to:
advanced tools (p)
edit Hybrid MBR (h)
Select your GPT partitions that you want on your MBR (you can select max 3), in your case just type "2 3 4" without quotes
Partition types are: AF for partition 2, 07 for other 2 (even if one has Linux)
Add protected "something" for first partition (used for grub): Y
Write (w)

Reboot, you should have your Linux bootable. Don't resync using refit if it is working!

Can't be more precise as I'm at work and don't have access to my mac.

Cheers

So I've started on building the hybrid MBR, and it gives me the following option:

"Place EFI GPT (0xEE) partition first in MBR (good for GRUB)? (Y/N)"

I chose to put the 0xEE partition first.

So now, which partitions should I put the "Bootable Flag" on?  If I choose yes for "Set the bootable flag?" for each partition, will rEFIt still be happy?  I'm not sure how rEFIt reads the partitions.

---

### Post by ozxto on 2012-01-17
Never mind, everything's up and running now.  Thanks for your help!

---

### Post by scognito on 2012-01-18
> **ozxto said:**
> Never mind, everything's up and running now.  Thanks for your help!

Yes, my "Add protected 'something' for first partition (used for grub): Y"  was meant for "Place EFI GPT (0xEE) partition first in MBR (good for GRUB)? (Y/N)"
No need to set bootable, I'm glad you got it working :)

---

### Post by ozxto on 2012-01-18
> **scognito said:**
> Yes, my "Add protected 'something' for first partition (used for grub): Y"  was meant for "Place EFI GPT (0xEE) partition first in MBR (good for GRUB)? (Y/N)"
No need to set bootable, I'm glad you got it working :)

Actually I did set bootable for each partition, and it still ended up working fine.  Would you recommend me rewriting the MBR and not setting the bootable flag for each?  Or does it not matter?

Btw, just for laughs I checked the partition tool in rEFIt, and it wants to change the MBR from:
Partition 1:  EFI
Partition 2:  AF
Partition 3:  07
Partition 4:  07

To:
Partition 1:  EFI
Partition 2:  AF
Partition 3:  07
Partition 4:  83

(This is just a crude representation).  It basically just wants to change the hex code of partition 4 (Ubuntu) from 07 to 83 without changing any bit ranges or hex codes of the other partitions.  I remember you saying above not to resync using rEFIt if it worked.  What I'm wondering is would anything happened if I changed the code to 83 (Linux Filesystem) rather than 07 (Microsoft Basic Data).  In fact, why set the Ubuntu partition to Microsoft Basic Data in the first place out of curiosity?  

Thanks again for your help, I just have these couple of questions about the process.

---

### Post by scognito on 2012-01-18
> **ozxto said:**
> Actually I did set bootable for each partition, and it still ended up working fine.  Would you recommend me rewriting the MBR and not setting the bootable flag for each?  Or does it not matter?

Btw, just for laughs I checked the partition tool in rEFIt, and it wants to change the MBR from:
Partition 1:  EFI
Partition 2:  AF
Partition 3:  07
Partition 4:  07

To:
Partition 1:  EFI
Partition 2:  AF
Partition 3:  07
Partition 4:  83

(This is just a crude representation).  It basically just wants to change the hex code of partition 4 (Ubuntu) from 07 to 83 without changing any bit ranges or hex codes of the other partitions.  I remember you saying above not to resync using rEFIt if it worked.  What I'm wondering is would anything happened if I changed the code to 83 (Linux Filesystem) rather than 07 (Microsoft Basic Data).  In fact, why set the Ubuntu partition to Microsoft Basic Data in the first place out of curiosity?  

Thanks again for your help, I just have these couple of questions about the process.

There is no need to change, 83 or 07 are the same for refit. I initially tough to change to 83 too because it is more correct, but since it works i prefere to leave it as is, same for bootable flags :)

---

### Post by notmyreal on 2012-06-25
please excuse the long reply but my difficulties seem to belong most here:

I installed rEFIt, and (I think) it successfully created a Hybrid MBR (or at least am partway toward creating one), and upon rebooting the Macbook Pro the rEFIt menu shows up and works fine and the original OSX install is still working, but the newly created Partition was only 200MB, which clearly isn't big enough for a Windows7 install (which is my first goal, to be followed by creating more Partitions to facilitate a Triple-Boot with Ubuntu, Win7, and Snow Leopard on an '11 Macbook Pro).  

and I have been trying to follow these threads for tips but am having issues:

* [http://ubuntuforums.org/showthread.php?t=1910328](http://ubuntuforums.org/showthread.php?t=1910328)
* [http://refit.sourceforge.net/tripleboot/](http://refit.sourceforge.net/tripleboot/)
* [http://forums.macrumors.com/showthread.php?t=1336597](http://forums.macrumors.com/showthread.php?t=1336597)

Namely… upon seeing the new Partition is only 200MB I tried using diskutil > resizevolume to simultaneously shrink the OSX Partition and create two new Partitions (for Win7 and Ununtu respectively) using the following (I am, clearly, a novice to these tools but have done many similar things on the Win platform… please let me know if I'm making some obvious rookie mistake) using the following:

diskutil resizevolume /dev/disk0s2 465.3G "MS-DOS FAT32" "Ubuntu" 10G "MS-DOS FAT32" "Windows" 20G

which started out fine but threw the following error:

"Started partitioning on disk0s2 Macintosh HD
Verifying disk
Error: -9915: Could not modify partition map because filesystem verification failed"

after that I tried a few things a few times each…

* using gdisk to delete the 200MB partition to try to start over (works fine, didn't help)
* firing up BootCamp (doesn't work, I forget the error)
* uninstalling and reinstalling rEFIt (easy and repeatable, but no help)
* various attempts to use diskutil > resizevolume (with varying degrees of success)

and now… I'm back to a (seemingly) successfully installed rEFIt, and OSX works fine,  but with a deleted 200MB Partition (I did this previously), but most notably the following evidence that something is jacked up with the MBR/Partition table:

using gdisk from a Terminal it's currently reporting only one Partition via p (print partition table), which is the correct number of Partitions but...:

Number  Start (sector)    End (sector)  Size       Code  Name
   2          409640       976248839   465.3 GiB   AF00  Customer

and a contradictory report from diskutil from a Terminal which reports:

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                  Apple_HFS Macintosh HD            499.6 GB   disk0s2

and Disk Utility GUI from OSX 10.6.8 reporting and throwing the following error:

- it only sees one Partition, 499.63GB on the Partition tab

- and the Verify Disk button throws the following errors:

"This disk needs to be repaired. Start up your computer with another disk (such as your Mac OSX installation disc), and then use Disk Utility to repair the disk."

and the details say:

"Verifying volume “Macintosh HD”
Performing live verification.
Checking Journaled HFS Plus volume.
Checking extents overflow file.
Checking catalog file.
Checking multi-linked files.
Checking catalog hierarchy.
Invalid directory item count
(It should be 33 instead of 32)
Checking extended attributes file.
Checking volume bitmap.
Checking volume information.
The volume Macintosh HD was found corrupt and needs to be repaired.
Error: This disk needs to be repaired. Start up your computer with another disk (such as your Mac OS X installation disc), and then use Disk Utility to repair this disk."

so, what gives?

What is the accurate description of its current state (other than jacked up…)?

and, how do I:

(A) get the HD/MBR/Partition Table back to factory state such that I can start over from the beginning (without harming the current OSX install which is still fine)?

and/or

(B) get from here to a successfully resized/shrunk OSX Partition and the creation of the other Partitions needed to facilitate the Win7 and Ubuntu installations in triple boot via rEFIt?

I/we have been seemingly getting closer over the last few days but seem to be dancing around the outside, almost getting it right, but something is clearly wrong.  Please help.

Thanks in advance…

---

