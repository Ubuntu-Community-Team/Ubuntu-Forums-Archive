---
title: "Manual partitioning fails on Mac Pro"
date: 2010-08-24
forum: Apple Hardware Users
---

### Post by m-ito on 2010-08-24
Hi everyone,

I'm installing Ubuntu 10.04.1 on my Mac Pro 4 (2x Quad-core Intel Xeon, Mac OS X 10.6.2 ).  But manual partitioning fails with the error message "ubi-partman failed with exit code 141".

Before getting the error, I followed the steps 1,2,3 in [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot: Mac OSX and Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot: Mac OSX and Ubuntu)

[INDENT]1. Install rEFIt 
2. Use Bootcamp to create another partition at the end of the disc. 
3. Boot the Ubuntu LiveCD (ubuntu-10.04.1-desktop-amd64.iso) and start the partition editor (gparted) under System > Adminstration. Use gparted to delete the partition just made by Bootcamp. Apply changes.[/INDENT]

Then I confirmed that the last partition became 'unallocated'. So I started the ubuntu-installer by clicking its icon, and after choosing "Specify partitions manually", the installation stopped with that error message.

Of course, in case of choosing "Use the largest continuous free space", the installation was successfully done. But I need  to customize partitions.

Does anybody know how to fix this problem?  

Thanks in advance.

---

### Post by srs5694 on 2010-08-24
I'm not positive, but my suspicion is that you've got a damaged hybrid MBR. This seems to be an extremely common problem lately. Check [this thread,]("http://ubuntuforums.org/showthread.php?t=1559105") and in particular my message #8 in that thread. If you need more help, post the output of "sudo fdisk -l" at a command prompt in the installer.

---

### Post by m-ito on 2010-08-24
Thank you very much for telling me about the possibility of a damaged hybrid MBR, and for guiding me into the informative thread. 

Here's the output from 'sudo fdisk -l' which I did in the terminal of LiveCD environment.

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26        8234    65929216   af  HFS / HFS+
/dev/sda3            8234       77825   558995276+  ef  EFI (FAT-12/16/32)
ubuntu@ubuntu:~$ 
```hmmm, there's no overlap between partitions. Does this mean a reasonable hybrid MBR?

---

### Post by srs5694 on 2010-08-25
Yes, that looks reasonable, although "fdisk -lu" will give you more precision in partition start and end points. (Without the -u option, fdisk reports partition start and end points in cylinders rather than in sectors.) Clearly you don't have the huge problem with the multiple overlapping 0xEE partitions that others have reported. Perhaps posting the output of "gdisk -l /dev/sda" would be informative. (You'll need to either boot from a utility disc that includes gdisk, such as System Rescue CD or Parted Magic; or use apt-get to install the gdisk package from an Ubuntu Live CD boot.)

---

### Post by m-ito on 2010-08-26
Thank you for the reply. I've succeeded in manually partitioning my Mac Pro HDD to install Ubuntu 10.04.1. 

After reading your comments in [that thread]("http://ubuntuforums.org/showthread.php?t=1559105"), I thought that the hybrid MBR in my Mac Pro was not so damaged. So I did cut-and-try method until succeeding in manual partitioning.

The following is how I've installed ubuntu-10.04.1-desktop-amd64.iso into a Mac Pro 4 (2x Quad-core Intel Xeon, Mac OS X 10.6.2 ).

1. Put 'Mac OS X Install DVD' into the Mac Pro, and restart. Use DiskUtility to clean up the whole HDD and to make two partitions (one is Mac OS extended (journaling), the other is MS-DOS(FAT)). Reinstall Mac OS X
2. Install rEFIt
3. Reboot and update the MBR using 'Start Partition Tool' in rEFIt menu
4. Boot from Ubuntu LiveCD, and choose [ Install Ubuntu 10.04.1 LTS ]. When prompted, choose 'Specify partitions manually ' to prepare partions such like :

```
Device      type     Mount point      Size

---------------------------------------------------------
/dev/sda
free space                                    0
/dev/sda1   fat32                           209 MB
/dev/sda2   hfs+                         640000 MB
free space                                    0
/dev/sda3   ext4      /                  510388 MB   
/dev/sda4   swap                          65536 MB
free space                                    0
```

5. On the 'Ready to install' dialog, click [Advanced] button, and choose to install the boot loader to /dev/sda3
6. Reboot and choose 'Boot Linux from partition 3' from rEFIt menu
7. Enjoy.

The difference from [the first procedure I tried]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot: Mac OSX and Ubuntu") is to clean up the whole HDD and to make two partitions in the re-installation process of Mac OS X. I still don't see why this works and the first one doesn't.

---

### Post by m-ito on 2010-08-26
In case the above procedure may have damaged the hybrid MBR of my Mac Pro, let me post the output from 'fdisk -lu' and 'gdisk -l'.

```
$ sudo fdisk -lu /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2          409640   125409639    62500000   af  HFS / HFS+
/dev/sda3   *   125411328  1122263039   498425856   83  Linux
/dev/sda4      1122263040  1250263039    64000000   82  Linux swap / Solaris

$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 1250263728 sectors, 596.2 GiB
Disk identifier (GUID): ABAC7C66-5042-4C47-A33B-9118550ABCA1
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1250263694
Total free space is 2349 sectors (1.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       125409639   59.6 GiB    AF00  Macintosh HD
   3       125411328      1122263039   475.3 GiB   0700  
   4      1122263040      1250263039   61.0 GiB    8200  

```

I suppose the hybrid MBR is reasonable, and wish that installing Ubuntu on Mac Pro would be easier.

---

### Post by srs5694 on 2010-08-26
Yes, your hybrid MBR looks reasonable (at least, to the extent that the word "reasonable" can be applied to hybrid MBRs at all). I can't explain why your second attempt succeeded where your first attempt failed; I can only speculate that there was some subtle problem with your disk that either I've missed or that isn't apparent in the utility output you've posted.

---

