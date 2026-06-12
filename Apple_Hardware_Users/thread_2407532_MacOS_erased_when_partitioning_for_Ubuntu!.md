---
title: "MacOS erased when partitioning for Ubuntu!"
date: 2018-12-05
forum: Apple Hardware Users
---

### Post by dxscorp on 2018-12-05
Hey everyone,

Just looking for some advice for my situation... I was partitioning my drive to install Ubuntu, and an error occurred in MacOS while disk utility was running. Now my boot loader doesn't show MacOS nor does it show my Windows partition, and all I have available is Ubuntu!

I'd love to save the data on my Mac partition however I don't really know where to start when I can't even find it to try to boot into it. I have an external hard drive that I can clone to to try and preserve things, but I'd like to try to recover the files. I'm not sure this is even possible, I'm worried that the partitions were corrupted somehow.

Any help at all would be greatly appreciated! I'm currently on Ubuntu 16.04.

All the best

---

### Post by gsahli on 2018-12-05
Have you tried the Ubuntu disk utility - Disks?

---

### Post by oldfred on 2018-12-05
Do not know Mac, but these should still work.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)
Screenshots of several of the recovery tools
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) 
    
Post these:
sudo parted -l
sudo gdisk -l /dev/sda

---

### Post by dxscorp on 2018-12-19
> **oldfred said:**
> Do not know Mac, but these should still work.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)
Screenshots of several of the recovery tools
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) 
    
Post these:
sudo parted -l
sudo gdisk -l /dev/sda


```
~$ sudo parted -l
[sudo] password for jabe: 
Model: ATA APPLE SSD SM0512 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                  Flags
 1      20.5kB  210MB  210MB   fat32        EFI System Partition  boot, esp
 2      210MB   226GB  225GB                Customer
 3      226GB   236GB  10.6GB
 4      236GB   261GB  24.9GB  ext4
 5      261GB   500GB  239GB   ntfs         BOOTCAMP              msftdata

```

```
~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 977105060 sectors, 465.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 6625D52E-3248-44F7-9C31-A3421877B923
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 977105026
Partitions will be aligned on 8-sector boundaries
Total free space is 262186 sectors (128.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       440713151   210.0 GiB   FFFF  Customer
   3       440713152       461436927   9.9 GiB     FFFF  
   4       461436928       510046302   23.2 GiB    8300  
   5       510308352       977104895   222.6 GiB   0700  BOOTCAMP


```

I have rEFInd installed on my machine, and it only shows Ubuntu. When I hold alt on my mac to see its boot options, there is nothing there and entering network recovery mode seems to yield nothing useful.

Does it seem like the MacOS partition is corrupted, or maybe it's just not being accessed properly?
Would it be possible to copy the Mac partition to an external HDD and simply restore from that?

Thanks a ton for the help!

---

### Post by oldfred on 2018-12-19
What is the customer partition?

You are not showing any NTFS partitions for Windows.
Older Mac had gpt for Mac and MBR for older Windows that would not boot in UEFI mode. But hybrid not recommended & newer Windows (since Windows 7) can be installed in UEFI boot mode.
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by kevin160 on 2018-12-20
I assume that the files you want to recover are on the macOS partition?

I don't have windows installed on my laptop, but I do have High Sierra and Ubuntu set up using rEFInd.  My partition data looks like this:

FROM LINUX:

```
Number  Start   End    Size    File system  Name                    Flags
 1      20.5kB  210MB  210MB   fat32        EFI System Partition    boot, esp
 2      210MB   101GB  100GB
 3      101GB   210GB  109GB   zfs          Solaris /usr & Mac ZFS
 4      210GB   250GB  39.9GB  ext4
 5      250GB   250GB  134MB   hfs+         Booter

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       196661295   93.6 GiB    FFFF  
   3       196661296       410272127   101.9 GiB   BF01  Solaris /usr & Mac ZFS
   4       410273792       488134655   37.1 GiB    8300  
   5       488134984       488397127   128.0 MiB   AB00  Booter


```

FROM MACOS:

```
 /dev/disk0 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *250.1 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:                 Apple_APFS Container disk1         100.5 GB   disk0s2
   3:                        ZFS alumiumP                109.4 GB   disk0s3
   4:           Linux Filesystem                         39.9 GB    disk0s4
   5:                 Apple_Boot Boot OS X               134.2 MB   disk0s5

/dev/disk1 (synthesized):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      APFS Container Scheme -                      +100.5 GB   disk1
                                 Physical Store disk0s2
   1:                APFS Volume alumiumD                56.0 GB    disk1s1
   2:                APFS Volume Preboot                 44.9 MB    disk1s2
   3:                APFS Volume Recovery                1.0 GB     disk1s3
   4:                APFS Volume VM                      4.3 GB     disk1s4


```

As you can see, I have a boot partition that you don't.  It is my understanding that this partition is required to boot macOS High Sierra and Mavericks since the change to APFS.  You have two APFS partitions (2 and 3, with type FFFF).  

Hopefully this means that your data is recoverable.  

Options for recovery include (in order of preference):

Boot from your Time Machine backup drive.  You have one, right?  RIGHT?!?!?!  ;-)
Boot your mac in Target Disk mode and connect it to another mac with FireWire or Thunderbolt to copy files.
Physically remove your drive and connect it to another mac to copy the files.
Create a bootable external macOS HD on another mac and boot your mac from that to recover files.
Use Internet Recovery to format an external disk and then use Terminal to copy files.

---

