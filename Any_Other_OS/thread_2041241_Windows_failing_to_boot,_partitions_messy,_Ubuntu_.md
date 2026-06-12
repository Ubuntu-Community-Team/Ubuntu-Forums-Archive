---
title: "Windows failing to boot, partitions messy, Ubuntu Grub has taken over."
date: 2012-08-12
forum: Any Other OS
---

### Post by doobieboobie on 2012-08-12
:( Someone please help with this report, I'm a beginner to this whole two OS thing. I really just started getting into computers recently and silly me is now about to use boot repair to fix my partitions, Windows 7 won't boot...I picked the dual boot option on a Live CD installation of Backtrack 5 instead of "erase disk" I thought it would successfully add both backtrack and windows 7 but instead has caused an error, I've already searched numerous hours on the BT forums, but no help, PLEASE guys I need your assistance very fast. 

View my report and tell me wht I can do to fix this... [http://paste.ubuntu.com/1142517/](http://paste.ubuntu.com/1142517/)

---

### Post by darkod on 2012-08-12
1. Stop booting from that hdd right away!!! Looks like the windows partition is really messed up. In fact, it's not reported at all.

2. I don't know BT, so make a live cd of ubuntu and boot it into live mode (Try Ubuntu). Don't install it, just boot it into the live mode.

3. From there you can try to scan your hdd with testdisk and hopefully restore the win7 partition. Let us know when you get there and if you need more help.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I don't know hat the BT installer did, but according to the fdisk results of the partitions, that doesn't look like dual boot at all. You only have linux partitions, not ntfs partitions.

---

### Post by doobieboobie on 2012-08-12
Erghhh that doesn't sound too good.   Ok, where can I get the iso for Ubuntu so I can get the live CD? the only way I can talk to you guys through here is if I use the Mozilla browser from BT, or just my mobile web from my phone. Also can I use the windows installation disk to possible solve my problem?   EDIT: how exactly do I stop booting from the HDD right away to avoid anymore problems?

---

### Post by oldfred on 2012-08-12
You should be able to boot any liveCD or repairCD or USB. But some liveCDs also mount swap which may write into the swap area on the drive.
But I think you may still have your NTFS partition, but it just is mislabeled in the partition table. Three different ways looking at sda1 from boot script and two show NTFS and partition table says Linux.

```
sda1: ________________________________

    File system:       [COLOR=Red]ntfs[/COLOR]
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

/dev/sda1    *          2,048   476,927,914   476,925,867  [COLOR=Red]83 Linux[/COLOR]

/dev/sda1        CEBC55E8BC55CB99                      [COLOR=Red] ntfs[/COLOR]      
```I do not know BT, but in Ubuntu you might just be able to in disk utility change sda1 to 07 for NTFS.

I would backup partition table first:

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by doobieboobie on 2012-08-13
@oldfred hmm hopefully the partition is just mislabeled 

.....well I just finished getting the Ubuntu Live CD burned, I also have this iso for Windows 7 Premium installation  but I can't seem to move it from that Mozilla browser in BT that  I was referring to. Anyway, about the testdisk and Ubuntu live, could you guys give me step-by-step on what to do? Should I backup my partition *first*?

---

### Post by oldfred on 2012-08-13
Backups whenever making some sort of system change are always important. Some like image backups and that can make it very easy to restore, but I just backup my data and assume I will do a clean install. 

I would try Disk Utility from the Ubuntu liveCD first. It can just write the 07 to the partition table without reformating. Use edit partition and change type. 

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by doobieboobie on 2012-08-13
Okay so  I'm trying to backup my partition to the external device with the terminal command, ' sudo sfdisk -d/dev/sda > PTsda.txt ' but it responds with  

"Warning: extended  partition does not start at a cylinder boundary. DOS and Linux will interpret the contents differently."

Although I checked the home folder and the txt.file was sitting right there. 

Also for diskutility I attempted to change the label to HPFS/NTFS (0x07) but it said (error: The daemon is being inhibited) 


Lastly, I used partimage to save an image and it just saved the used memory of sda1 which was about 44MiB, anyway to backup the entire thing?

---

### Post by oldfred on 2012-08-13
Drives have not used cylinders since LBA. LBA started with drives over 8GB about 15 years ago. Now it is 8 sector boundaries for the new 4K and SSD type drives. You can ignore that error on cylinders.

You were only backing up the partition table not the partitions. But copy partition table file  to another device.

Your sda1 is about half the drive or 250GB, not sure what you got with 44MiB? If it is saying that is the used memory, that sounds like you may be missing data or confusion on type is causing issues.

Post in code tags (highlight like copying and click on # in edit panel above message) the PTsda.txt file. Code tags preserve formatting to make it easier to read.

You can see what testdisk says also.

This may work also,  but assumes you are in an install on the hard drive, not liveCD. Your BT should work.

change sda1 to type 07 note spaces:
sudo sfdisk --change-id /dev/sda 1 07

Not sure if it is 07 or 7 in above. 
see this for more info on sfdisk: 
man sfdisk

---

### Post by doobieboobie on 2012-08-14
Here is the txt file that you wanted:   ```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=476925867, Id=83, bootable
/dev/sda2 : start=476927998, size=499845122, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=958955520, size= 17817600, Id=82
/dev/sda6 : start=476928000, size=464209920, Id=83
/dev/sda7 : start=941139968, size= 17811456, Id=82
```Also, I'm currently in TestDisk, I found my partitions..all of them were deleted :( , looks like I still have most files though. I don't wanna  mess anything up again, so let me know exactly what to do to put my partitions back in order please!

[I]Deeper search: deleted partitions

[/I]```
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
 D HPFS - NTFS              0  32 33    25 159  6     409600
 D HPFS - NTFS              0  32 33 29687  99 13  476925857
D HPFS - NTFS             25 159  7 55089 252 11  884609024



```[I]

Quick search: partition table 
[/I]```
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
>* HPFS - NTFS              0  32 33 29687  99 13  476925857
 P Linux                29687 100 46 58583  32  9  464209920
 P Linux Swap           58583  64 42 59691 245 58   17811440
 L Linux Swap           59692  56 13 60801  79 62   17817584





```

---

### Post by oldfred on 2012-08-14
Deeper search is just showing the older partitions. Your issue is with sda1. Testdisk says it sees it as NTFS. I might see if you can get testdisk to just rewrite the partition table as it now sees it.

Otherwise we will have to manually edit the sfdisk output and reinput it. We only have to change the 83 to 07 or  7 for sda1 and import the updated file. But see what testdisk does first.

---

### Post by doobieboobie on 2012-08-14
Oh okay, I see.

Btw, Voila! I used your genius code to change the Id/partition table type back to 07, it worked. Impressive....
 :)

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=476925867, Id= 7, bootable
/dev/sda2 : start=476927998, size=499845122, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=958955520, size= 17817600, Id=82
/dev/sda6 : start=476928000, size=464209920, Id=83
[dev/sda7 : start=941139968, size= 17811456, Id=82
```

Although, Im not sure, it seems like sda1 partition is larger than the disk drive size. 
I got this error when I looked in diskutility :

```
Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sda, start=1048576, new_start=1048576, new_size=244186043904, type=0x07
Error: command not found
ubuntu@ubuntu:~$ Entering MS-DOS parser (offset=0, size=500107862016)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ MSDOS_MAGIC found
MSDOS_MAGIC: command not found
ubuntu@ubuntu:~$ looking at part 0 (offset 1048576, size 244186038784, type 0x07)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ new part entry
No command 'new' found, did you mean:
 Command 'ne' from package 'ne' (universe)
 Command 'znew' from package 'gzip' (main)
 Command 'nex' from package 'nvi' (universe)
 Command 'net' from package 'samba-common-bin' (main)
 Command 'nes' from package 'mednafen' (universe)
 Command 'nes' from package 'fceu' (universe)
 Command 'news' from package 'sysnews' (universe)
 Command 'nw' from package 'netrw' (universe)
new: command not found
ubuntu@ubuntu:~$ looking at part 1 (offset 244187136000, size 237675479040, type 0x83)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ new part entry
No command 'new' found, did you mean:
 Command 'ne' from package 'ne' (universe)
 Command 'znew' from package 'gzip' (main)
 Command 'nex' from package 'nvi' (universe)
 Command 'net' from package 'samba-common-bin' (main)
 Command 'nes' from package 'mednafen' (universe)
 Command 'nes' from package 'fceu' (universe)
 Command 'news' from package 'sysnews' (universe)
 Command 'nw' from package 'netrw' (universe)
new: command not found
ubuntu@ubuntu:~$ looking at part 2 (offset 481863663616, size 9119457280, type 0x82)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ new part entry
No command 'new' found, did you mean:
 Command 'ne' from package 'ne' (universe)
 Command 'znew' from package 'gzip' (main)
 Command 'nex' from package 'nvi' (universe)
 Command 'net' from package 'samba-common-bin' (main)
 Command 'nes' from package 'mednafen' (universe)
 Command 'nes' from package 'fceu' (universe)
 Command 'news' from package 'sysnews' (universe)
 Command 'nw' from package 'netrw' (universe)
new: command not found
ubuntu@ubuntu:~$ looking at part 3 (offset 490983413760, size 9130060800, type 0x0f)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ Entering MS-DOS extended parser (offset=490983413760, size=9130060800)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ readfrom = 490983413760
readfrom: command not found
ubuntu@ubuntu:~$ MSDOS_MAGIC found
MSDOS_MAGIC: command not found
ubuntu@ubuntu:~$ Exiting MS-DOS extended parser
Exiting: command not found
ubuntu@ubuntu:~$ Exiting MS-DOS parser
Exiting: command not found
ubuntu@ubuntu:~$ MSDOS partition table detected
MSDOS: command not found
ubuntu@ubuntu:~$ containing partition table scheme = 0
containing: command not found
ubuntu@ubuntu:~$ got it
No command 'got' found, did you mean:
 Command 'go' from package 'golang-go' (universe)
 Command 'gout' from package 'scotch' (universe)
 Command 'jot' from package 'athena-jot' (universe)
 Command 'git' from package 'git' (main)
 Command 'gpt' from package 'gpt' (universe)
 Command 'gom' from package 'gom' (universe)
 Command 'goo' from package 'goo' (universe)
 Command 'gst' from package 'gnu-smalltalk' (universe)
 Command 'dot' from package 'graphviz' (main)
 Command 'god' from package 'god' (universe)
got: command not found
ubuntu@ubuntu:~$ Error: Can't have a partition outside the disk!
> ped_disk_new() failed
> 

```

---

### Post by oldfred on 2012-08-14
Which command was it that worked?

NTFS partitions also have the start & size info in the PBR or partition boot sector. Often chkdsk and/or fixBoot from a Windows repairCD or full install disk are required.

Testdisk can rewrite a basic NTFS PBR, but Windows 7 usually needs to re-repair it as testdisk seems to write the XP version.

---

### Post by doobieboobie on 2012-08-14
This code:

 sudo sfdisk --change-id /dev/sda 1 07

By the way, are you saying thas  I will need to get a window repair disc as opposed to a windows installation disc, or the other away around?

And if I need to get either one, /am I required to clean install/format or can I restore my windows tht I had before my computer got all effed up?

---

### Post by oldfred on 2012-08-14
You need the recovery console in Windows to run repairs. I do not think the Vendor recover DVDs have that, but if you have the full install DVD/CD or have made a repairCD then you can get the recovery console.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

You probably need chkdsk and maybe fixboot.

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

If you run auto repairs or fixMBR then you will directly boot Windows which may be ok to confirm it is ok, but will then have to use Ubuntu liveCD to repair grub2 in the MBR.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

or Manually.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by doobieboobie on 2012-08-14
Welp...

burned and made the repair disk, fixmbr nor chkdsk worked, zero installations were found....

as pissed as I am right now, I'll just have to reinstall.
If you have any more ideas, please let me know.

But I would  also like to know how to get BT off of my partitions,  it has messed up my entire computer, no more dual boot for me. Windows single boot from here on out.

---

### Post by oldfred on 2012-08-14
Is boot flag still on sda1, the NTFS partition?

If you run fixMBR that will install the Windows boot loader, but I think it has to find your Windows install. Did you run chkdsk, then fixBoot, then maybe chkdsk again? Also if chkdsk finds any error you have to re-run it as it does not fix everything on one pass.

You can use gparted from Ubuntu liveCD to remove Linux partitions. But you have to have the Windows boot loader installed first. And you can use Windows to expand its partition if you want. I always partition in advance just so I know what partition changes are being made. That is no guarantee that everything will work but often is better.

You can install to another external drive or even a flash drive if over 8GB if you want to try other systems.

---

### Post by doobieboobie on 2012-08-15
Nope, no boot flag on sda1, its says Id =7, bootable, it also says sda4 does not start on physical boundary ? And its Id is f and running  on W95 (LBA) the rest is Linux..

Im confused though, everytime I run gparted it displays no partition table, just unallocated I didn't delete it or format it at all. This makes me feel like chkdsk is pointless because all I might be doing is checking free space, right? :confused:

---

### Post by doobieboobie on 2012-08-15
]Nope, no boot flag on sda1, its says Id =7, bootable, it also says sda4 does not start on physical boundary ? And its Id is f and running  on W95 (LBA) the rest is Linux..[
Im confused though, everytime I run gparted it displays lo parttion table, just unallocated I didn't delete it or format it at all. This makes me feel like chkdsk is pointless because all I might be doing is checking free space, right? :confused:

And I ran chkdsk twice, one before fixboot and one right after, it fixed my MBR but I still can't boot.

---

### Post by oldfred on 2012-08-15
The bootable is the boot flag.

The extended partition does not have to start on a physical boundary. the f,  is the code for the extended partition which is fine.

But if gparted still will not show any partitions then there still is a partition error. And often with partition table errors nothing works on partitions as they see the error and stop working (like gparted is).

From Boot-Repair run the BootInfo as it often highlights partition table errors. 

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by doobieboobie on 2012-08-15
[http://paste.ubuntu.com/1149765/](http://paste.ubuntu.com/1149765/)

Above is yet another report, sigh.

bootable = boot flag, oh okay, that clears alot of things up.

---

### Post by oldfred on 2012-08-15
I have seen both testdisk & various Windows partition tools write a bad partition table.

From script:
> /dev/sda4 ends after the last sector of /dev/sda

First backup partition table and copy this to some other drive as a backup of current partition table:
sudo sfdisk -d /dev/sda > parts_sda.txt

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by doobieboobie on 2012-08-15
Okay so fixpart worked, I wrote my partition table to the disk, and its now displaying on GParted.

I just ran fdisk -u and it says this: 
```

The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.
```So should I resize my partitions? Shrink them?

Also isn't the boot sector for sda1  suppose to start at 0, I just checked Gparted and it said sda's first sector is at 2048.

---

### Post by oldfred on 2012-08-15
No, the area after the MBR or sector 0 is used by grub, Windows and many others to store boot info, serial number and other info.

With XP and older versions of Ubuntu sda1 would default to a start of sector 63. Both Windows  and Ubuntu now use sector 2048 as the new default first sector for sda1 for better compatibility with SSD, and the new 4K drives.

Do you have a newer 4K drive as that sometimes does cause issues as some software tools still do not correctly handle them or BIOS/drive defaults do not match system.

---

### Post by doobieboobie on 2012-08-16
4k drive? Yeah I believe so.

---

### Post by oldfred on 2012-08-16
What does this show?

sudo parted /dev/sda unit s print

---

