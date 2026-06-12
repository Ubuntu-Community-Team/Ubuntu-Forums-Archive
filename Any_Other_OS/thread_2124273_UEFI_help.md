---
title: "UEFI help"
date: 2013-03-10
forum: Any Other OS
---

### Post by SimonaZ on 2013-03-10
Hi, linux newbie here.

I've installed the ubuntu-based Mint, and now I cannot boot into Windows.
I'm satisfied with the system and I wouldn't really care about that if I could optimize battery life (still working on it).

Asus laptop. 64Bit OSes, both Mint and Windows 7.
Two 1TB hard drives (=2TB worth of space).

The laptop didn't come with a recovery CD.
Nor is the recovery partition working (messed up batch files, I tried fixing it several months ago but decided that it's not wroth the hassle).

The error is 
"invalid EFI file path"

I've already run Ubuntu's boot repair from the live cd.
But that doesn't really help.

I'm following this guide:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Here are the logs
[http://paste.ubuntu.com/5599570/](http://paste.ubuntu.com/5599570/)

---

### Post by Perfect Storm on 2013-03-10
Moved to Other OS/Distro Talk.

---

### Post by SimonaZ on 2013-03-10
Ah sorry, I thought the other sub forum was to be used for all ubuntu-based distors

---

### Post by oldfred on 2013-03-10
It looks like Boot-Repair tried to convert a BIOS install on sdb to UEFI. But UEFI has to have gpt partitions and only sda is gpt. Not sure if booting in UEFI with Linux on sdb in BIOS/MBR mode would work or not.

Does Mint boot?

Was system Windows 8 with secure boot and you down graded to Windows 7? 
If originally Windows 7, you should not have secure boot and Boot-Repair then would not have to rename Windows boot files.

With secure boot and systems that then only boot the Windows files Boot-Repair renames files.
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

If you do not have secure boot then you should not have renamed files. Not sure if another run of Boot-Repair un-renames them or not. Try un ticking the secure boot and then run rename files.

With your current configuration of gpt and UEFI on sda and MBR(msdos) on sdb, about the only way to boot is to install Mint in BIOS mode on sdb. Then each time you want to change, you have to go into UEFI menu and turn on or off UEFI or BIOS mode to boot the other system. Boot systems have to be BIOS or both UEFI to easily dual boot.

      
 Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by SimonaZ on 2013-03-10
Mint is loading just fine.

I bought the laptop in the summer (that means that Windows 8 was still in beta; I'm not sure, though, as I never pay attention to Microsoft releases), so that probably means that I don't have Secure Boot (I tried looking for it in the BIOS - it's not there; it is my understanding that Secure Boot is W8 feature, though). 

I did not rename anything myself; running the live CD was the first thing I'd done.
I have had Boor-repair run twice, to check if it would work on a second run.

As stated above, I don't have Secure-Boot (or perhaps it's just named differently? I'll post the features available to me in the BIOS).

I'm going to try the advanced settings now.

---

### Post by oldfred on 2013-03-10
I am suprised Mint boots from MBR with a UEFI boot. But good to know. It really is just grub that is different between UEFI(grub-efi) & BIOS (grub-pc).

If Boot-Repair does not name files back. Does UEFI menu show both Linux & Windows as boot options?

These are the normal boot files:
 # UEFI Boot files UEFI sees folder for efi files, so it will show, ubuntu, Windows, Boot and maybe others for recovery.
# from Ubuntu full mount path where normal mount is /boot/efi - /boot/efi/EFI/ubuntu/grubx64.efi 
/efi/ubuntu/grubx64.efi
# New secure boot grub version:
/efi/ubuntu/ shimx64.efi.
# for Windows, but for UEFI systems that only boot this file, grub or shim may get renamed to this and this backed up.
/EFI/Microsoft/Boot/bootmgfw.efi
# Both Windows & Ubuntu may provide this shell file, not sure of differeneces.
/efi/Boot/bootx64.efi
efi shell
\EFI\BOOT\BOOTX64.EFI. 
# There also may be other files in each directory to support booting.

And you should have a copy:

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by SimonaZ on 2013-03-10
Here's what I see:
[http://i.imgur.com/cgK43ie.jpg](http://i.imgur.com/cgK43ie.jpg)

And yes, such file C:\Windows\Boot\EFI\bootmgfw.efi exists

what should I do?

---

### Post by oldfred on 2013-03-10
Your menu looks like a mix of UEFI and BIOS entries.

If you boot this directly from UEFI menu does it boot Windows.
 /EFI/Boot/bkpbootmgfw.efi 

    
That should be the same file as the original bootmgfw.efi and/or you can copy the original from c: to efi partition. Back up efi partition first before renaming or copying files. Boot-Repair has copied this shim file to be the bootmgfw.efi file so those Windows 8 systems with secure boot think they are booting Windows. The shim has the Microsoft key and is supposed to work with all secure boot systems, but some modified UEFI to only boot the bootmgfw.efi file.

 # New secure boot grub version:
/efi/ubuntu/ shimx64.efi

---

### Post by SimonaZ on 2013-03-10
not sure i understand.

what exactly is uefi menu ?

I can add boot options in BIOS, is that what you want me to do?

or should i do it through grub?

btw, I can open the Win recovery, don't remember which one tho
it seems to load for around one minute 
but then comes back to grub

---

### Post by oldfred on 2013-03-10
Technically there is no more BIOS. But we have UEFI with CSM. But I still call it BIOS sometimes too.
       UEFI Compatibility Support Module (CSM)

Do you have secure boot off? Some UEFI will only boot with secure boot off, others work with it on or off. Grub's shim file has the Microsoft key and it should work, but some make it difficult.

And then from BIOS can you directly boot?

---

### Post by SimonaZ on 2013-03-10
i don't have secure boot option..

and i can't load directly

---

### Post by oldfred on 2013-03-10
If you are sure you do not have secure boot - It is only on new systems with Windows 8 pre-installed, then from Boot-Repair uncheck the secure boot tick and rerun the rename files. That should change names back to defaults.

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.
I disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by SimonaZ on 2013-03-11
Done this,

now the errors are:

"error: no such device: 38D2-86AD.
error: file 'EFI/Boot/bkpbootx64.efi' not found."

[http://paste.ubuntu.com/5604853/](http://paste.ubuntu.com/5604853/)

PS: Mint still loads ok

---

### Post by oldfred on 2013-03-11
That is the correct partition. gpt partitions look ok, but you have the error on the protective MBR. gpt has a protective MBR which is just the first sector on the drive like standard MBR(msdos) partitioning. It exists only so old disk tools see the drive is fully partitioned with gpt.

Not sure if gdisk will update protective MBR or not.

sudo apt-get gdisk

run it and issue the w command to write partition table. Since it will see gpt part as ok, I am not sure it will update MBR.
For more info on using gdisk.
       GPT fdisk Tutorial 
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by SimonaZ on 2013-03-11
Am I doing something wrong?

ubuntu@ubuntu:~$ sudo gdisk /dev/sda1
GPT fdisk (gdisk) version 0.8.6

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************

Exact type match not found for type code 7200; assigning type code for
'Linux filesystem'
Entering GPTPart::SetName(const UnicodeString...)
Exact type match not found for type code 6500; assigning type code for
'Linux filesystem'
Entering GPTPart::SetName(const UnicodeString...)
Exact type match not found for type code 7900; assigning type code for
'Linux filesystem'
Entering GPTPart::SetName(const UnicodeString...)
Exact type match not found for type code 0D00; assigning type code for
'Linux filesystem'
Entering GPTPart::SetName(const UnicodeString...)

Warning! Secondary partition table overlaps the last partition by
3805500090 blocks!
You will need to delete this partition or resize it in another utility.

Command (? for help): w

Warning! Secondary partition table overlaps the last partition by
3805500090 blocks!
You will need to delete this partition or resize it in another utility.

Problem: partitions 2 and 1 overlap:
  Partition 2: 168689522 to 2104717761
  Partition 1: 778135908 to 1919645538

Problem: partitions 3 and 1 overlap:
  Partition 3: 1869881465 to 3805909656
  Partition 1: 778135908 to 1919645538

Problem: partitions 3 and 2 overlap:
  Partition 3: 1869881465 to 3805909656
  Partition 2: 168689522 to 2104717761

Problem: partitions 4 and 3 overlap:
  Partition 4: 2885681152 to 2885736650
  Partition 3: 1869881465 to 3805909656
Aborting write operation!
Aborting write of new partition table.

Command (? for help): p
Disk /dev/sda1: 409600 sectors, 200.0 MiB
Logical sector size: 512 bytes
Disk identifier (GUID): 93E03241-A2FC-49DF-BFAC-13108AED30E0
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 409566
Partitions will be aligned on 1-sector boundaries
Total free space is 409533 sectors (200.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1       778135908      1919645538   544.3 GiB   8300  Linux filesystem
   2       168689522      2104717761   923.2 GiB   8300  Linux filesystem
   3      1869881465      3805909656   923.2 GiB   8300  Linux filesystem
   4      2885681152      2885736650   27.1 MiB    8300  Linux filesystem

Command (? for help):

---

### Post by oldfred on 2013-03-11
I hope you pressed q. As nothing in new gpt table looks correct. Did you use sda1 not sda. You have to use drive not a partition, and that may be entire error?

According to BootInfo gpt table looked ok, it was just the MBR table that had issues. And we definitely do not want MBR converted into a new incorrect gpt table.

What does parted and gparted say?

       sudo parted /dev/sda unit s print

---

### Post by SimonaZ on 2013-03-11
Yeah, I did press Q.
I used /dev/sda1. (I'll try to use sda now.)

sudo parted /dev/sda unit s print
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start        End          Size         File system  Name                          Flags
 1      2048s        411647s      409600s      fat32        EFI system partition          boot
 2      411648s      673791s      262144s                   Microsoft reserved partition  msftres
 3      673792s      782084095s   781410304s   ntfs         Basic data partition
 4      782084096s   1902323711s  1120239616s  ntfs         Basic data partition
 5      1902325760s  1953524129s  51198370s    ntfs         Basic data partition

---

### Post by oldfred on 2013-03-11
Parted looks ok, what does gdisk now say with sda?

---

### Post by SimonaZ on 2013-03-11
ubuntu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.6

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Should I W now?

---

### Post by oldfred on 2013-03-11
Yes, since it seems to see it correctly. Not sure still if it will update protective MBR.

---

### Post by SimonaZ on 2013-03-11
ubuntu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.6

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): Y
OK; writing new GUID partition table (GPT) to /dev/sda.
Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, or the disk might be damaged! Checking it is advisable.

Command (? for help): v

No problems found. 5067 free sectors (2.5 MiB) available in 3
segments, the largest of which is 2048 (1024.0 KiB) in size.

Command (? for help): i
Partition number (1-5): 1
Partition GUID code: C12A7328-F81F-11D2-BA4B-00A0C93EC93B (EFI System)
Partition unique GUID: CC17E3D7-FB34-45F0-AD03-8ECEA7E2EBFD
First sector: 2048 (at 1024.0 KiB)
Last sector: 411647 (at 201.0 MiB)
Partition size: 409600 sectors (200.0 MiB)
Attribute flags: 8000000000000000
Partition name: 'EFI system partition'

Command (? for help): i
Partition number (1-5): 2
Partition GUID code: E3C9E316-0B5C-4DB8-817D-F92DF00215AE (Microsoft reserved)
Partition unique GUID: EAAFCDA5-635F-4ED2-9843-97D693650CA0
First sector: 411648 (at 201.0 MiB)
Last sector: 673791 (at 329.0 MiB)
Partition size: 262144 sectors (128.0 MiB)
Attribute flags: 8000000000000000
Partition name: 'Microsoft reserved partition'

Command (? for help): i
Partition number (1-5): 3
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 069A8FCB-C6B0-4132-B647-3FACEE23BE88
First sector: 673792 (at 329.0 MiB)
Last sector: 782084095 (at 372.9 GiB)
Partition size: 781410304 sectors (372.6 GiB)
Attribute flags: 0000000000000000
Partition name: 'Basic data partition'

Command (? for help): i
Partition number (1-5): 4
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 9AB47C3E-118F-4A65-A1A4-C4F41572A345
First sector: 782084096 (at 372.9 GiB)
Last sector: 1902323711 (at 907.1 GiB)
Partition size: 1120239616 sectors (534.2 GiB)
Attribute flags: 0000000000000000
Partition name: 'Basic data partition'

Command (? for help): i
Partition number (1-5): 5
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 953E9D96-8916-4F33-8137-8BC9999A2220
First sector: 1902325760 (at 907.1 GiB)
Last sector: 1953524129 (at 931.5 GiB)
Partition size: 51198370 sectors (24.4 GiB)
Attribute flags: 0000000000000000
Partition name: 'Basic data partition'

PS: Windows still doesn't boot :(

---

### Post by oldfred on 2013-03-11
Rerun BootInfo report.

I do not know if it fixed protective MBR partition table and even it that was issue.

---

### Post by SimonaZ on 2013-03-12
Not sure if it's the correct thing but:

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start        End          Size         File system  Name                          Flags
 1      2048s        411647s      409600s      fat32        EFI system partition          boot
 2      411648s      673791s      262144s                   Microsoft reserved partition  msftres
 3      673792s      782084095s   781410304s   ntfs         Basic data partition
 4      782084096s   1902323711s  1120239616s  ntfs         Basic data partition
 5      1902325760s  1953524129s  51198370s    ntfs         Basic data partition

ubuntu@ubuntu:~$

---

### Post by oldfred on 2013-03-12
That does not show protective MBR.

This will not show gpt partitions but shows MBR with just its one entry Which should not be larger than hard drive.

sudo fdisk

---

### Post by SimonaZ on 2013-03-12
Not sure what exactly to type there in, but 

ubuntu@ubuntu:~$ sudo fdisk /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): p

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2902cc6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

---

### Post by oldfred on 2013-03-12
It did not change.

Does gparted show partitions correctly. I might just try a very minor change or just shrink one partition by a small amount.

---

### Post by SimonaZ on 2013-03-12
[IMG]http://i.imgur.com/St9xS99.png[/IMG]

What do you mean shrink one partition?
Which exactly?
sda1? Will shrinking it by one mb suffice?

---

### Post by oldfred on 2013-03-12
I would use sda4 as it is the largest and not very full. And as the test to see if gparted will rewrite protective MBR, a 1MB shrink should be enough.

---

### Post by SimonaZ on 2013-03-13
Resized by 8mb. Didn't help

I'm starting to give up:)

---

### Post by oldfred on 2013-03-13
Rerun Boot-Repair and post a new link to BootInfo report.

---

### Post by SimonaZ on 2013-03-13
[http://paste.ubuntu.com/5611902/](http://paste.ubuntu.com/5611902/)

Doesn't work :lolflag:

This is comical at this point.. hehe
why did they have to make it this complicated.

I've never had any such problems before uefi was introduced

---

### Post by oldfred on 2013-03-13
It just may be that Mint does not have enough support for UEFI with secure boot. Even with secure boot off we are seeing systems that just do not want to work or require users to leap thru hoops to get it to work.

---

### Post by SimonaZ on 2013-03-13
Well, that's good enough.

Thank you for trying to help! :P

I'll go ask around on other forums, and even if that doesn't work out, then I'll just remove my W7 partition and forget about dual-booting.

I'll post again in case I find a solution.

---

### Post by SimonaZ on 2013-03-19
Dropping by to say that I've "fixed" the problem.

Well... my "solution" was to re-install Windows 7.
I used [these]("http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/how-do-i-repair-my-windows-7-installation-the/b027b64f-1c11-4c72-aff4-db4ad4710d90") ISO files.
It's legit; you only have to have your Windows product key in tact.

After getting Windows up and running I've installed [Easy BCD]("http://neosmart.net/EasyBCD/").

Both systems now work correctly.

This isn't exactly a "fix". More of a work-around.

Regardless.
Thank you for your help, [COLOR=#c61919]oldfred. :)[/COLOR]

---

