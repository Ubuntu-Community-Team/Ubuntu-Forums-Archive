---
title: "Unrecognized Partition"
date: 2009-11-25
forum: Apple Hardware Users
---

### Post by JohnAtilano on 2009-11-25
I've successfully installed Ubuntu 9.10 on my MacBook Pro (5,1).  Everything appears to be working fine.  However, rEFIt, is reporting that the partitions are out of sync and will not touch this disk.  I have a couple of images to show the unrecognized partition (disk0s3).

Is this a problem?  Does it need to be fixed? I so, how?

Thanks in advance for any help you can provide.

---

### Post by linuxopjemac on 2009-11-26
I am not an expert on this, but this small 1 Mb partition looks weird to me. It seems that Grub is there or something while the Linux root is in the 4th partition. I have read earlier problems like this. You can  try to set the boot flag to the Linux root from within gparted (the partitioning tool) on the liveCD, then you might be able to sync later from rEFIt. Just try, it won't do harm.

---

### Post by jacobs444 on 2009-11-26
If your system boots and performs as expected, then no this is not a problem, and you can simply ignore!

---

### Post by JohnAtilano on 2009-11-26
Tried to run gptsync but I still get the same message as I do in rEFIt.  This extra 1.0MB rrpartition, I believe is where I installed GRUB during the initial installation of Ubuntu.  Per directions, choose "Advanced" in last step and choose /dev/sda3 instead of hd0.

rEFIt sees Linux as a "Legacy OS on partition 3."  Any other thoughts to a solution here?

$ sudo gptsync /dev/sda
Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    910311463  Mac OS X HFS+
 3      910311464    910313417  Unknown
 4      910313418    973946230  Basic Data
 5      973946231    976773134  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    910311463  af  Mac OS X HFS+
 3 *    910311464    910313417  00  Unknown
 4      910313418    973946230  83  Linux

Status: GPT partition of type 'Unknown' found, will not touch this disk.

---

### Post by Nohtanhoj on 2009-11-26
Give this thread a read. Many people have the same problem as you do (including me for a while).

[http://ubuntuforums.org/showthread.php?t=1297229](http://ubuntuforums.org/showthread.php?t=1297229)

Good luck!

---

### Post by JohnAtilano on 2009-11-28
Thanks!  While the solution did sync the GPT and MBR, the unrecognized partition remains.  I know it is only 1MB but nothing in any of the documentation I have read indicates that this is normal behavior.  As an experiment, I deleted the partition.  This nuked my system.  I got a black screen that said "Missing Operating System" and a blinking cursor when I tried to boot Ubuntu.  Mac OS X was fine.  I reinstalled and the 1MB partition was created again.  Here is the the partition list from Disk Utility (on the Mac).

$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS MacHD                   467.5 GB   disk0s2
   3: 21686148-6449-6E6F-744E-65656445                         1.0 MB     disk0s3
   4:       Microsoft Basic Data                         31.0 GB    disk0s4
   5:                 Linux Swap                         1.4 GB     disk0s5

Any other ideas as to why this extra partition is being created?

---

### Post by Nohtanhoj on 2009-11-28
I have no concrete answers, but I can venture a hypothesis, my only evidence being that deleting the partition nuked your system. In my opinion, it's one of two things:

1. GRUB resides on that partition, and deleting this would obviously kill your boot process.

2. Linux's EFI signature resides on that partition, and since Macs use EFI, Linux is not recognized as an OS. This is the more probable reason, as you can see a small EFI partition that has been created for OS X. I'd say that Linux did the same thing...

Like I said, I don't have any concrete ideas, but why worry about this partition? It's only 1 MB... =D

---

### Post by JohnAtilano on 2009-11-29
So after further investigation it appears this partition is the MBR (see attachment).

My concern is not with the loss of 1MB; my concern lies with the non-standard partition scheme which differs from everyone else on this board.  While I am not having problems now, my fear is that it could lead to problems later on.

Secondly, I installed Ubuntu to learn.  This is the first of many learning opportunities.  If I just accept this, I wont be able to help out another newb, like myself, who may encounter the same problem.

Third, clearly I did something differently which resulted in a different result.  I'd like to figure out what that was.

Finally, I've always approached learning from the following axiom: "The man who knows how will always have a job; the man who knows WHY will always be his boss."  I'll never master Linux if I don't understand the "why."

Thanks for everyone' help and patience.  Any additional help you can provide would be most appreciated.

gptsync output:

$ sudo gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    913486735  Mac OS X HFS+
 3      913486736    913488689  BIOS Boot Partition
 4      913488690    974072674  Basic Data
 5      974072675    976773134  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    913486735  af  Mac OS X HFS+
 3 *    913486736    913488689  da  Non-FS data
 4      913488690    974072674  83  Linux

Status: Tables are synchronized, no need to sync.

---

### Post by v.cecchetto on 2009-11-30
Happy you have solved.

If you are interested i can light the question a little.

The new partition scheme GPT is born to substitute the old MBR partition scheme.

MBR is all contained in the first 512 bytes of the hd, the so called first sector (LBA 0). MBR is made of: boot code + 4 partition entry

For historical reason the first partition that you create starts from the sector 64 (LBA 63).

(A great source of information about disk and boot process: [http://mirror.href.com/thestarman/asm/mbr/index.html](http://mirror.href.com/thestarman/asm/mbr/index.html))

The sector through LBA 1 to LBA 63 are free.

GRUB is a boot loader. Its code reside in: MBR code area (first sector - LBA 0), and it makes use of some of the sectors free (LBA 1 - LBA 63).

GPT is quite different from MBR. No code area, only partition entry. You can have 128 partition entry. GPT reside in sector LBA 1 - LBA 33.

GPT not use the first sector (LBA 0). Normally programs that handle GPT store in this sector a protective MBR writing, in the first of the 4 partition entry, a big partition that cover all the disk size. The programs that doesn't know how to handle GPT read that fake MBR partition scheme and knows that all the disk is covered by a partition and doesn't touch it.

The first partition that you create on a GPT disk starts from sector LBA 34.

If you want to install GRUB (grub2 knows how to handle GPT) on a GPT disk, it claims that it cannot find place to write himself, in fact all the sectors are used (LBA 0 -> protective MBR, LBA 1/33 -> GPT, First Partition LBA 34...)

How can you install grub2 so?
You have to reserve a little space in the hard disk so grub2 can install its code in it. You than create a little raw partition (with no file system) in the disk. The type of this partition must be BIOS BOOT. 
When you want to install grub2 you than type:

$ sudo grub-install /dev/sda

With this command you let grub install its code in the MBR like usual and the remaining part of code in this recognized BIOS BOOT partition. 

On my pc i have a BIOS BOOT partition (8MB - raw) and another little partition (200MB - ext3) where i installed the /boot directory of ubuntu. The /boot directory is the place where grub store all the other code and configuration files it needs. 

If you loose the BIOS BOOT partition not a problem. Create another one and reinstall on it grub with the above command.

To handle GPT partition in linux i suggest to not use gparted but gdisk ([http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)).

If you want to install WINDOWS 7 on a gpt disk you have to use hybrid MBR instead of protective MBR, go to the link i posted for more information. If you install WINDOWS 7 on an hybrid MBR disk you doesn't need the Microsoft Reserved Partition ([http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)).

EFI partition that you have is a partition used by Apple.

EFI is a standard born to substitute the old BIOS. It promise a fast boot ([http://blog.laptopmag.com/phoenixs-1-second-instant-boot-bios-really-works](http://blog.laptopmag.com/phoenixs-1-second-instant-boot-bios-really-works)).

EFI platform make use of GPT disk. EFI platform need to reserve a partition, the so called EFI partition. EFI needs this partition because it is complex and want to handle personally the devices on the computer and so it needs a place to put its personal device drivers. At least is what i have read somewhere, if my memory is good. Someone sure can more precisely explain this.

If you have an EFI motherboard on your pc you can install WINDOWS 7 directly on a GPT disk (you need also the EFI partition and the Microsoft Reserved Partition), instead you have to use hybrid MBR. 

To have a dual boot system on my BIOS - GPT system i worked really hard... thx you Microsoft guys.

---

