---
title: "Mint EFI boot problems"
date: 2012-03-24
forum: Any Other OS
---

### Post by niglas on 2012-03-24
Followed all the steps but I get:

```
**mint@mint /boot/efi $** sudo modprobe efivars
**mint@mint /boot/efi $** grub-probe --target=device /boot/efi/efi/grub/grub.efi
Segmentation fault
**mint@mint /boot/efi $** sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label "GRUB2" --loader "\\EFI\\grub\\grub.efi"
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.

**mint@mint /boot/efi $** sudo grub-probe --target=device /boot/efi/efi/grub/grub.efi
**mint@mint /boot/efi $** sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label "GRUB2" --loader "\\EFI\\grub\\grub.efi"
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
```Any ideas what I did wrong?

---

### Post by oldfred on 2012-03-24
Moved to separate thread in otherOS, since it looks like Mint.

It was this thread which was solved and is now older info anyway.
[http://ubuntuforums.org/showthread.php?t=1903323](http://ubuntuforums.org/showthread.php?t=1903323)

Often users do not look at solved threads unless they are looking for a solution, not to provide a solution. Best to have your own unsolved thread.

Not sure what version of grub2's efi installer your version of Mint is using. Grub2 & efi installer have progressed a lot recently and older versions may not work well as they had a lot of bugs. New version do not require any recompiling.

Where are you at, have you installed and cannot boot, or cannot install.

If installed post this.

The git/testing version has some fixes:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```
or this which also runs git version of boot info script:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

If you have not installed post this & if not sda change to your drive:
sudo parted /dev/sda unit s print
gdisk -l /dev/sda

---

### Post by niglas on 2012-03-24
Thanks!

Installation works fine, but I cannot boot.

Interesting sections from the files:

gdisk:
```
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          390659   190.7 MiB   EF00  
   2          390660        39453160   18.6 GiB    0700 

```parted:
```
Model: ATA OCZ-AGILITY3 (scsi)
Partition Table: gpt

Number  Start    End        Size       File system  Name  Flags
 1      34s      390659s    390626s    fat32              boot
 2      390660s  39453160s  39062501s  ext4

```bootinfoscript:
```
sda1: __________________________________________________________________________
    File system:       vfat
    Boot sector type:  Grub2 (v1.99)

sda2: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 12 Lisa
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1                   1   117,231,407   117,231,407  ee GPT

GUID Partition Table detected.
Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       390,659       390,626 EFI System partition
/dev/sda2         390,660    39,453,160    39,062,501 Data partition (Windows/Linux)

```

---

### Post by niglas on 2012-03-24
The boot-repair program tells me:
> The boot of your PC is in BIOS mode. Please change it to EFI mode. Then try again.

How do I do that?

---

### Post by oldfred on 2012-03-24
I have seen posts where users said there was no setting, or maybe they could not find it. But those seem to try to boot from the efi partition in UEFI mode and then if not found boots from MBR in BIOS mode.

Others have posted that there is a setting in BIOS/UEFI on how it boots.

Boot info script is missing a lot or you do not have system installed?

---

### Post by niglas on 2012-03-24
> **oldfred said:**
> I have seen posts where users said there was no  setting, or maybe they could not find it. But those seem to try to boot  from the efi partition in UEFI mode and then if not found boots from MBR  in BIOS mode.

Others have posted that there is a setting in BIOS/UEFI on how it boots.


There's an option in UEFI/BIOS:
```
PCI ROM Priority

[LIST]
[*]EFI Compatible Rom
[*]Legacy Rom
[/LIST]
 
```...I haven't found any other setting than that.


> **oldfred said:**
> 
Boot info script is missing a lot or you do not have system installed?

I do have the system installed. But I thought the output was quite long to post, so I attached the files of the full output and posted the most interesting sections instead. Did you find anything suspicious in the output files?

---

### Post by oldfred on 2012-03-24
I am sure legacy ROM  then means the old BIOS boot and the other obviously is the UEFI that uses the efi partition to boot.

I have never actually done it:

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

some other links where they got it to work:

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

---

### Post by niglas on 2012-03-24
I have tried to follow 5-6 guides of how to do it. It all seems to come down to the sentence:
> This requires the kernel to be booted in UEFI mode...
...which I don't really know what it means, after that step it always fails.

That is probably what [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") complains about too.

---

### Post by oldfred on 2012-03-24
Is grub2 installed to the efi partition? 

Post the link to the full boot info script that Boot-Repair creates.

---

### Post by niglas on 2012-03-25
When I follow [these steps]("http://ubuntuforums.org/showpost.php?p=11620595&postcount=8") in hope for the os to recognize the ESP automatically and install grub on it:

[LIST]
[*]Gdisk states that GPT is present on the disk.
[*]But I don't see the grub files when I mount the ESP.
[/LIST]

When I follow [these]("https://help.ubuntu.com/community/UEFIBooting#Building_GRUB2_.28U.29EFI") or [these]("http://ubuntuforums.org/showpost.php?p=11598988&postcount=7") steps I get the fault as in [the first post of this thread]("http://ubuntuforums.org/showpost.php?p=11790191&postcount=1").


The full output of the bootinfoscript is attached in the [third post of this thread]("http://ubuntuforums.org/showpost.php?p=11790522&postcount=3") ("RESULTS.txt").

---

### Post by oldfred on 2012-03-25
You have grub installed to the MBR as if in BIOS mode. And a install to the partition boot sector.

Newer posts say you do not have to recompile grub with Ubuntu, but what version of grub2 are you using? Or what Ubuntu is your Mint based on.

I still do not see full boot script. Boot Repair creates a link. Just post link.

Just to get you booting create a new 1MB partition anywhere on drive and flag it with bios_grub. Reinstall grub2's boot loader to the MBR and set to boot in BIOS mode.

If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. 

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

If you're using EFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-2TB disks, so you may need to use another utility to do the partitioning.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

---

### Post by niglas on 2012-04-14
I finally managed to boot with EFI, I wrote a guide of how I did it:
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

Thanks for all the help!

---

