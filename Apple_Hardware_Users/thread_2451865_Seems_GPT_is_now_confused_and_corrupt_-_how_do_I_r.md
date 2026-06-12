---
title: "Seems GPT is now confused and corrupt - how do I recover my data?"
date: 2020-10-12
forum: Apple Hardware Users
---

### Post by briandu2 on 2020-10-12
Hi,
I am using a 2014 Mac Mini with **Ubuntu** 20.04 (default install) on a USB connection (1 TB SSD)
This has been working fine for approx a week. Just when I am ready to consider a backup of the drive it somehow will not boot up.
Actually previously the Mac would boot into a small OSX drive - pressing the Mac alt button (on start up) allows one to boot into other drives. This has been working fine and then became erratic.

I booted from a USB boot stick and used gparted which reflects /dev/sdb1 and /dev/sdb3 as filesystem unknown.

Using a small spare drive I installed Ubuntu again and it erratically worked until I re-installed it again with the following partitions using **gdisk**
/dev/sb1 as EFI   +512M
/dev/sdb2 as fs_boot +512M
/dev/sdb3 as fs_root (the rest of the drive)

new install Ubuntu with other (manual partitions) and formatting sdb1 as EFI, sdb2 as /boot and sdb3 as /root.
Once installed and rebooted then went ```
cd /boot/efi/EFI/ubuntu
``` and executed ```
mv shimx64.efi shimx64.efi_old
``` and ```
cp grubx64.efi shimx64.efi
```; then reboot and all the strange messages  such as "Failed to set Mok........" at bootup.

This seems quite robust and consistently boots up directly or using the Mac alt key choices.   Point is it works properly and no problems.

**HOWEVER**, I have the problem with my 1TB drive:
Booting up from the small drive gparted still states the partitions are unknown.
I use **gdisk**

```
sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sdb: 2000409264 sectors, 953.9 GiB
Model: Name            
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): A0D13BCD-15E6-4EA3-A70F-554583C1CC7D
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 2000409230
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   EF00  EFI System Partition
   2         1050624      2000408575   953.4 GiB 
```

it seems fine but if I use
```
sudo gdisk /dev/sdb1
[sudo] password for xxxxx: 
GPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Warning! Secondary partition table overlaps the last partition by
1999360033 blocks!
You will need to delete this partition or resize it in another utility.
```

and

```
Command (? for help): p
Disk /dev/sdb1: 1048576 sectors, 512.0 MiB
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): CD527C6A-F72B-48BE-88F0-A7C45C98A77A
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1048542
Partitions will be aligned on 2048-sector boundaries
Total free space is 1048509 sectors (512.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2         1050624      2000408575   953.4 GiB   8300  Linux filesystem
```

as can be seen it reports number **2** and not **1!**

using option **p** results in -

```
Command (? for help): p
Disk /dev/sdb1: 1048576 sectors, 512.0 MiB
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): CD527C6A-F72B-48BE-88F0-A7C45C98A77A
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1048542
Partitions will be aligned on 2048-sector boundaries
Total free space is 1048509 sectors (512.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2         1050624      2000408575   953.4 GiB   8300  Linux filesystem
```

still number **2 **followed by **v**

```
Command (? for help): v                                           

Problem: partition 2 is too big for the disk.

Warning! Secondary partition table overlaps the last partition by
1999360033 blocks!
You will need to delete this partition or resize it in another utility.
```

Identified 2 problems!

it is a mess and if I follow through with **/dev/sdb2 **then

```
sudo gdisk /dev/sdb2
GPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Warning! Secondary partition table overlaps the last partition by
1050657 blocks!
You will need to delete this partition or resize it in another utility.
```

 and selecting** p** results in:

```
Disk /dev/sdb2: 1999357952 sectors, 953.4 GiB
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): F35C490F-3BAC-40B6-A2F1-C42BB23B0EF5
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1999357918
Partitions will be aligned on 2048-sector boundaries
Total free space is 1050590 sectors (513.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2         1050624      2000408575   953.4 GiB   8300  Linux filesystem
```

and selecting **v** results in - 

```
Problem: partition 2 is too big for the disk.

Warning! Secondary partition table overlaps the last partition by
1050657 blocks!
You will need to delete this partition or resize it in another utility.
```

Identified 2 problems!

As such I cannot afford to lose the sdb2 partition; although it is 900GB it is only using approx 200GB and I planned to shrisk the partition and the dd it over  to a spare drive. It is the only copy now and I cannot recreate it.

My **question** is what are my options?
[LIST=1]
[*] can I use gparted and delete the sdb1 partition and recreate it? If so how do I do that as gparted does not seem to set all the correct flags (yes I have latest updates and still cannot do so)
[*]Should I use boot-repair? From my trials in the sm I got it to work after installing Ubuntu in default install (thus only having a EFI and root partition) - I found this quite unreliable but I could get it to boot up.  Later, I shrunk the root partion and added aan additiona 512M partition; then applied the boot-repair, rebooted and it is what I am working from.   My concern is although I used a small disk in the trials I am unsure as to the imapct if any on the 1 TB /dev/sdb2 partition - I cannot afford to lose it
[*]Any other reliable options?
[/LIST]
I have read Rod's articles on gdisk/etc.  and many other posts from all over however there is a "Windows" flavour to them which is not my situation

Any views?

---

### Post by slickymaster on 2020-10-12
*Thread moved to **Apple Hardware Users**.*

---

### Post by oldfred on 2020-10-12
Check start & end, delete and recreate without overlap. Backup vital just in case.

last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)

---

