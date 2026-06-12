---
title: "Lost linux partition"
date: 2011-06-26
forum: Apple Hardware Users
---

### Post by eivindsm on 2011-06-26
Help!

I have dual booted my iMac with OS X 12.2 with ubuntu 11.04, only to find myself unable to locate the linux partition of the disk in OS X. I have a 1TB disk and during installation I allotted 700GB to the ubuntu partion. In ubuntu this volume is located at /dev/sda5. The system boots nicely with rFEIt.

In OS X: sudo diskutil list gives:
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:                 FDisk_partition_scheme          *1.0 TB   disk0
   1:                       0xEE                             209.7 MB   disk0s1
   2:                  Apple_HFS uten navn          300.0 GB   disk0s2
   3:             Windows_FAT_32 BOOTCAMP      38.7 GB  disk0s3
   4:                       0xEE                                 1.0 MB  disk0s4

In the disk utility tool the 700GB space is shown as free space at the end of the volume. Does anyone have any suggestions as to how I can update OS X with the correct partition table? 

This is how I installed:  
1) bootcamp to make an extra partition
2) installed rEFIt
3) from Ubuntu live CD I shrinked the Mac part of the disk
4) installed ubuntu (home sweet home)   

Greetings,
eivindsm

---

### Post by srs5694 on 2011-06-26
First, be ***very very very very careful!*** Your configuration is extraordinarily dangerous and it's possible your disk is already very badly damaged. OTOH, it's also possible your data aren't in any immediate danger, but if they are, you're taking a chance just by booting the computer....

The first problem you've got is that you seem to have a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) with two type-0xEE partitions. This is known to cause problems with OS X, causing it to be unable to see the GPT side of the disk, which is normally the "master" side for OS X and Linux, with only Windows using the MBR side. With the two-0xEE configuration, though, OS X uses the MBR partitions in preference to the GPT partitions.

That problem means that it's possible you've modified the MBR side without modifying the GPT side, which could result in a mish-mash of partitions that don't match on the two sides (MBR and GPT). If you try to fix this without proper analysis, you could end up making things worse, and if you use the disk at all and your partitions don't match, you could end up trashing one filesystem just by writing to another one. Thus, it's imperative that you analyze the disk completely and figure out what's what before you do anything else -- including booting *any* OS from that disk!

My recommendation is to do this:


[list=1]
[*]Boot using a Linux emergency disk, such as [PartedMagic,](http://partedmagic.com) [System Rescue CD,](http://www.sysresccd.org) or [RIP Linux.](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/) If this is your only computer and you don't happen to have such disks on hand, you can use the Ubuntu install disc in "live CD" mode; however, you'll need to install the gdisk package by typing "sudo apt-get install gdisk", and precede the below commands with "sudo".
[*]Launch gdisk on the disk in question by typing "gdisk /dev/sda" at a shell prompt.
[*]Type "v" in gdisk. This performs a disk verification, which will, among other things, check for consistency between the MBR and GPT sides.
[/list]


What you do from here depends on the results of the verification step. If gdisk reports that it could find no problems, then you should create a new hybrid MBR, as described [here,](http://www.rodsbooks.com/gdisk/hybrid.html) but be sure to *not* include a second 0xEE partition. I'd recommend including *only* the Windows partition(s) and any data-exchange partition(s) in the hybrid MBR and, if gdisk gives you the option, no extra protective partition. When you reboot, OS X should see the GPT side of the disk and it should start working normally -- or as normally as a hybrid MBR configuration ever works.

If, OTOH, gdisk's verification operation reports mis-matched GPT and MBR partitions, you should post back with details, as provided by the output of two commands:

```

gdisk -l /dev/sda
fdisk -lu /dev/sda

```

Be sure to post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags; if you don't, the columns won't line up, which makes it much harder to read the output.

Those two commands will show the GPT and MBR partition tables, respectively. With any luck it will be possible to figure out what's supposed to be what and repair the damage, but it may take further diagnostics to figure it out.

---

### Post by eivindsm on 2011-06-27
Hi,

thanks for your comprehensive instructions! First of all, I have a backup so I´m not that worried about my data. I guess worst case scenario is clean install, which will set me back a few hours.

I was unable to install gdisk with apt from the ubuntu live CD (its not in the 11.04 repository), so I installed and ran it from OSX The output:
```

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.

Command (? for help): p
Disk /dev/disk0: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 1AB3728C-0E32-4187-82D8-70E73E6ACA7A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 263598 sectors (128.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       586347111   279.4 GiB   AF00  uten navn
   3       586610688       662120046   36.0 GiB    0700  BOOTCAMP
   4       662120047       662122000   977.0 KiB   EF02  
   5       662122001      1945184501   611.8 GiB   0700  
   6      1945184502      1953525118   4.0 GiB     8200  

Command (? for help): v

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.

Caution: More than one 0xEE MBR partition found. This can cause problems
in some OSes.

Caution: Partition 4 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Caution: Partition 5 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Caution: Partition 6 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Consult http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/
for information on disk alignment.

No problems found. 263598 free sectors (128.7 MiB) available in 3
segments, the largest of which is 263576 (128.7 MiB) in size.


```

sudo gdisk -i /dev/disk0 gives:
```


GPT fdisk (gdisk) version 0.7.2

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/disk0: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 1AB3728C-0E32-4187-82D8-70E73E6ACA7A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 263598 sectors (128.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       586347111   279.4 GiB   AF00  uten navn
   3       586610688       662120046   36.0 GiB    0700  BOOTCAMP
   4       662120047       662122000   977.0 KiB   EF02  
   5       662122001      1945184501   611.8 GiB   0700  
   6      1945184502      1953525118   4.0 GiB     8200  

```

So what do you think, is it possible to fix the tables?

---

### Post by srs5694 on 2011-06-27
Yes, it seems that my worst-case scenario isn't playing out. I recommend you use gdisk to create a fresh hybrid MBR, as described on the [gdisk hybrid MBR page.](http://www.rodsbooks.com/gdisk/hybrid.html) I'd put /dev/sda3 in the hybrid MBR, and possibly /dev/sda5. (I'm guessing that /dev/sda3 is your Windows installation and /dev/sda5 is Linux. If that's correct, then /dev/sda5 need not be in the hybrid MBR.) You could add /dev/sda4 or /dev/sda6 to keep their space from being used by MBR tools, but don't bother adding /dev/sda2 -- if you omit it, the standard GPT protective partition will cover its space, thus protecting it from damage.

When you make this change, it's conceivable that Windows will refuse to boot. You should be able to fix this by running the Windows installation disc to fix the problem. You can minimize the chance of this happening by including another partition (I'd use /dev/sda5) *before* /dev/sda3 in the hybrid MBR -- that is, when you specify the partition numbers for inclusion in the hybrid MBR, type "5 3" (or "5 3 4" or "5 3 6" or whatever, so long as "3" is the second digit you type). Also, when prompted be sure to tell gdisk to put the GPT protective partition first in the MBR. This will keep /dev/sda3 as the 3rd entry in the MBR, where it is now.

---

### Post by srs5694 on 2011-06-27
Oh, one more point: The warnings about several partitions not beginning on 8-sector boundaries are important if you've got an Advanced Format disk, which uses 4096-byte physical sectors but which reports that it's got 512-byte sectors. See [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for details. Many, but not all, 1TB disks are Advanced Format models, so I can't say for sure if you're affected. If you are, you'll need to resize all your Linux partitions to avoid performance problems.

---

### Post by eivindsm on 2011-06-27
Great, I will try this!

There´s no Windows on the machine. The bootcamp partition was created but never used. According to instructions on the web it´s needed to get started, and can be deleted afterwords. I´m not sure why, though.

---

### Post by srs5694 on 2011-06-27
If there's no Windows installation, then you might want to check out my [page on EFI-booting Ubuntu on a Mac.](http://www.rodsbooks.com/ubuntu-efi/) It's possible to do this with absolutely no hybrid MBR, which is much less trouble-prone once you've got it working, in my experience. The problem is getting it set up in the first place, since many of the utilities and instructions on the Web assume a Boot Camp style installation.

---

### Post by eivindsm on 2011-06-27
Hi,

I decided to go for the EFI-booting solution and have gone through the steps 1-23 in your guide. However the EFI option in rEFIt boot menu tells me that there are no bootable device or something and redirects me back to rEFIt. Any ideas where this can have gone wrong? My partition table now looks like this:
```

Command (? for help): p
Disk /dev/disk0: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 1AB3728C-0E32-4187-82D8-70E73E6ACA7A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 75772957 sectors (36.1 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       586347111   279.4 GiB   AF00  uten navn
   4       662120047       662122000   977.0 KiB   EF02  
   5       662122001      1945184501   611.8 GiB   0700  
   6      1945184502      1953525118   4.0 GiB     8200  


``` 

Cheers!

---

### Post by eivindsm on 2011-06-27
Hi,

I decided to go for the EFI-booting solution and have gone through the steps 1-23 in your guide. However the EFI option in rEFIt boot menu tells me:
Starting grub.efi
Error: Unnsupported while loading grib.efi

Any ideas where this can have gone wrong? My partition table now looks like this:
```

Command (? for help): p
Disk /dev/disk0: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 1AB3728C-0E32-4187-82D8-70E73E6ACA7A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 75772957 sectors (36.1 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       586347111   279.4 GiB   AF00  uten navn
   4       662120047       662122000   977.0 KiB   EF02  
   5       662122001      1945184501   611.8 GiB   0700  
   6      1945184502      1953525118   4.0 GiB     8200  


```Cheers!

---

### Post by srs5694 on 2011-06-27
Your EFI-enabled boot loader probably didn't get properly installed to the ESP. Try the following diagnostic commands:

```

df -h /dev/sda1
sudo find /boot/efi -name "*efi"

```

If your ESP is properly mounted, the first command should return something like this:

```

/dev/sda1             197M   33M  165M  17% /boot/efi

```

If instead it returns something with "/dev" in the final column, your ESP isn't mounted, but it should be -- at least, for some of the steps on my Web page.

Note that the ESP is conventionally mounted at /boot/efi on Linux systems. I didn't fully realize this when I wrote my Web page; I should probably update it, although this detail isn't critical for proper installation of GRUB in EFI mode, depending on how it's done.

The second command returns a list of all the .efi files (which are EFI executables, most notably boot loaders) in /boot/efi -- that is, in the ESP, if it's mounted in the traditional place. (If you've mounted it elsewhere, such as at /mnt, you should adjust the command appropriately.) It should include an entry for grub.efi, or whatever other name you've given to GRUB. If that file is missing, you should review the procedure to figure out where it's gone and make whatever correction is necessary. Perhaps just moving files you created in the wrong place will do the trick.

---

### Post by eivindsm on 2011-07-01
Hi, I gave up EFI booting and started over with a clean install using rEFIt. 

I still have not achieved what I set out for though; to share my ubuntu home folder to OSX. I have synchronnized the UIDs for both user accounts, as described here:
[http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)

 and mounted /dev/sda5 (an ext3 partition) to /Volumes using fuse-ext2 as described her:
 [http://ubuntuforums.org/showthread.php?t=1688257&highlight=ext3](http://ubuntuforums.org/showthread.php?t=1688257&highlight=ext3)

The mount command returns without any messages, but /Volumes/ubuntu (the mount point) is empty! Any ideas or tips!?

---

### Post by eivindsm on 2011-07-03
Update in case anyone is interested.

I have now finally managed to have fully transparent partition shared between my to operating systems ubuntu 11.04 and OS X. To achieve this I had to spend $39 on a proprietary software called ExtFS by Paragon: [http://www.paragon-software.com/home/extfs-mac/](http://www.paragon-software.com/home/extfs-mac/)

ExtFS mounts ext2/ext3/ext4 filesystems on OS X, and it works on this iMac 12.2 with OS X 10.6.8.

Proprietary software goes against all my principles off course, but that´s what it takes to keep my wife happy I guess.

---

