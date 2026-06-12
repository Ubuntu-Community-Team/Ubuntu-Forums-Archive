---
title: "grub2 booting in UEFI mode"
date: 2013-04-18
forum: Any Other OS
---

### Post by flashback_rtk on 2013-04-18
Hello,

I have Linux Mint 13 (Ubuntu 12.04) installed on my PC with a UEFI motherboard and want to double boot with Windows 7. When partitioning the disk (1 TB), I left 250 GB of unallocated space for Windows. I set the disk to a GPT partition table. Before formatting I was asked to make an extra partition without any filesystem to install grub2 for a GPT partition table. I did so. The installation is functional.

When trying to install Windows, its partitioning software recognises the disk and all of its partitions. It also recognises the unallocated space. It's even possible to use the unallocated space and prepare the partitions for Windows. Anyway it won't let me install it saying it's not possible because my disk has a GPT partition table. Apparently the installation DVD can boot either on BIOS mode or UEFI mode, and the latter is needed to install the OS on a GPT disk. I have read that my UEFI BIOS should let me choose to start the DVD in either mode but it doesn't. The DVD has a boot file that's possible to reach via the UEFI shell. In that shell I see the block devices connected to the motherboard and I am able to mount the DVD, but when I try the commands 'ls' or 'cd' it says there's no directory to list.

I would like to know if the partition I made for it has some influence in the inability to boot the Windows DVD in UEFI mode. Since this happens before grub2 starts, I mostly think it's something to do with me, the UEFI settings and the UEFI shell, but I would like to rule out this possibility. 

My motherboard is an MSI with the Z77 chipset connected to an Ivy Bridge processor on socket 1155. The hard disk and the DVD drive are connected both to a SATA3 port. The DVD is of the UDF format. This is the output of the command 'parted -l':

```

Model: ATA WDC WD10EZEX-00R (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End     Size    File system     Name  Flags
 1      268GB  268GB   2000kB                        bios_grub
 2      268GB  269GB   268MB   ext2
 3      269GB  290GB   21,0GB  ext3
 4      290GB  292GB   2097MB  linux-swap(v1)
 5      292GB  1000GB  708GB   ext3


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

```

I would like to know if someone is spotting what's causing the problem, or if someone knows better about UEFI settings and double booting. 

Thank you very much in advance.

---

### Post by Perfect Storm on 2013-04-18
Moved to Other OS/Distro Support.

---

### Post by oldfred on 2013-04-18
You have Ubuntu installed in BIOS mode not UEFI. I use BIOS and gpt partitioning and have to have the bios_grub partition.

With UEFI boot you have to have an efi partition and it should be first. Windows 8 makes it second so not hard fast rule, but do not put it far into drive.

Windows will only boot from gpt partitioned drives with UEFI.
And if you want to easily dual boot you have to have both Windows & Ubuntu in either BIOS or both in UEFI.

Somewhere I read that Windows will install in either UEFI or BIOS when booted from flash drive, but not from DVD.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

    You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

If you create the efi partition at beginning of drive, Boot-Repair will convert a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi.
[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)

This does not include any space for Windows as most already have it.
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better  to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only  can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need  swap but having some is still recommended. I do not hibernate (boots  fast enough for me) but if hibernating then you need swap equal to RAM  in GiB not GB. And if dual booting with windows a shared NTFS partition  is also recommended. But you usually cannot create that as part of the  install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use  the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by flashback_rtk on 2013-04-25
Hello,

Thank you very much for the quick reply, and also sorry I couldn't answer earlier. 

There was a lot of things I didn't know, like the fact that my Ubuntu  installation is starting in BIOS mode because of the location of the  grub partition. Also I didn't  know it was compulsory to use an USB  stick to boot Windows in UEFI mode.

I would like to get some things clear before proceeding. Can I use  gparted (via a Live CD) and its ability to manipulate (move, resize...)  partitions to do all of it without losing any data?
As far as I understand I have to move the gpt boot partition (the one  without a filesystem) to the beginning of the disk, then run the  boot-repair CD to convert it to UEFI. Will this automatically make my  Ubuntu installation start in UEFI mode?
Then I have to set up a Windows install USB from the Windows DVD and  boot it in UEFI mode. Then part the unallocated space reserved for  Windows as stated in [http://technet.microsoft.com/en-us/l...8WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx") . Then I suppose Windows will overwrite the boot loader somehow. I have some questions regarding that:
Is it going to overwrite 2 MB grub partition or is it booting from its  own system partition (100 MB)? Can I use the boot-repair CD again to  have grub letting me choose the OS?

Regarding the partitions of the disk I plan to part it this way:
GPT partition table, all primary
1. grub (2 MB)
2. Windows System (with its 3 partitions) (between 150-200 GB)
3. Shared NTFS partition (Windows 'My Documents') (between 100-50 GB)
4. Linux /boot partition (I think it's 100 MB now)
5. Linux root partition (around 20 GB)
6. Swap partition (8 GB - same as my RAM)
7. /home partition (rest of the disk GB)

Is this layout correct/optimal? Should I put the swap partition before the root partition?

Thank you very much for your time.

---

### Post by oldfred on 2013-04-25
It is not a grub partition, but an efi (ESP) partition with UEFI and should be 250MB. The UEFI spec says it should be first, but Windows wants it repair partition first and most installs with Windows have it second. Must not be vital if first, but should be near start of drive.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Not sure how Windows installs if partitions are created in advance, but it needs its specific partitions. If you have to resize Windows NTFS partition use Windows disk tools, but use gparted for everything else.

      
 I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.
You should also install gdisk which is the fdisk equivalent for gpt drives. It is in repository.
sudo apt-get install gdisk
      
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


 In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

You also should not need the separate /boot. Otherwise your partitioning looks ok to me. I always put swap last but that was with MBR and in the extended and it kept it out of the way for changing other partitions. You may not need 8GiB for swap either. Only if you want to hibernate. Otherwise with 8GB you will probably never use swap but I still suggest some like 2GB.

---

### Post by flashback_rtk on 2013-04-29
Thank you very much, I am now able to dual boot Linux Mint 13 (Ubuntu 12.04) and Windows 7 both in UEFI mode. This thread can be marked as solved.

I prepared the Windows 7 USB as described in the tutorial. The Windows installer took care of formatting the unallocated space with a UEFI partition and the Windows partitions. Then I booted from the Mint Live CD and used boot-repair. First time it didn't work. Then (using gparted) I deleted my previous grub_bios partition and expanded (and moved) the next partition. I also checked the 'purge previous GRUB installs' when I ran boot-repair again. It created a start up file with the .efi extension in the UEFI partition. I had to run it from the UEFI shell (accessible at boot time via the graphical bios), which now showed filesystems by default (instead of only block devices), and I got a grub menu that let me finish to install Windows (and now run it) or launch Linux. After running that file now always boots into that gurb menu by default, and both installations work.

I have still have some questions about the partitions anyway. Maybe it's me but I've got the feeling that when in Linux the HDD makes more activity. Is that something related to having moved and resized the partition? It was just 2MB but I think this has more to do with alignment than size, right? Also, is there a way to 'defrag' or tidy up an ext3 filesystem (I know they are tidier than FAT or NTFS by default)? Is it what happens automatically in Ubuntu at boot time when mounted around 30 times?

Also, I made 2 NTFS partitions for Windows, one for the OS and programs and the other one for 'My Documents' folder to share with Linux. Anyway I am thinking of removing it because Linux can read the main C: partition and the bulk of files is gonna reside in the /home partition anyway. I have read that Windows becomes un-bootable. Is boot-reapair solving that? Will I get HDD performance penalty for expanding the Windows partition?

Thank you very much for your time, dedication and help, thanks to that I have my system working as I want. Kudos.

---

### Post by oldfred on 2013-04-29
I would keep the separate data partition.
The Linux NTFS drive exposes all normally hidden files & folders in Windows, so accidents are more likely. For whatever reason Windows does not seem to like too much writing into its system. It just may be users corrupting system or moving files they should not, but many seem to have issues. 
Best just to set Windows sytem partition as read only and use the NTFS data partition as read-write.

I think ext4 is a slightly better file system.
 Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

Linux does write into the file last access time unless turned off. We often turn that off for SSDs with noatime in fstab in place of the standard realatime. See man mount and man fstab.

Boot-Repair will not fix internal Windows issues. It may fix a MBR issue.
Best to have a Windows repair CD or flash drive.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

