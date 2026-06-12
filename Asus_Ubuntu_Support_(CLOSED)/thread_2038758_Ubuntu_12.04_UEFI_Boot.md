---
title: "Ubuntu 12.04 UEFI Boot"
date: 2012-08-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Insomniac0des on 2012-08-07
Hey Everyone,

         This is my first post in here, so please bear with me. Recently I have ordered parts for my new desktop. The Specs are:

          MoBo: **ASUS M5A97 AM3+ w/ UEFI BIOS  **
[COLOR=Blue]( [www.newegg.com/Product/Product.aspx?Item=N82E16813131767 )]("http://http://www.newegg.com/Product/Product.aspx?Item=N82E16813131767")[/COLOR]

CPU: **AMD Phenom II x4 965 BE**

          gfx Card: **Sapphire Radeon HD 6850 1 GB GDDR5 256 bit **
[COLOR=Black][( www.newegg.com/Product/Product.aspx?Item=N82E16814102908]("http://http://www.newegg.com/Product/Product.aspx?Item=N82E16814102908") )[/COLOR]

It has come to my notice that, there exists an ample amount of trouble with installing Linux (or Ubuntu in my case) with UEFI BIOS. So I would like to ask a few questions in regard to that:

Also, I plan to install it on a 120 gb SSD.


           1. **Can I install Ubuntu 12.04 by booting the LIVE CD in UEFI mode** ( I will have  Ubuntu 12.04 as the only OS on the system)

            2. **In some cases I have heard that the graphics drivers act up, which is why you have to use the integrated graphics and then install video-card drivers later on **? ( I am asking, because my motherboard doesn't have a on-board  video card)          

          I'm planning to put together the machine this Friday, so any information before that would be very useful. I just want the assembling and installing to go through seamlessly.

         Thank you all in advance.

---

### Post by oldfred on 2012-08-07
Are you installing Windows also? If booting UEFI, you will also want to create partitions in gpt mode not MBR(msdos). Gparted uses msdos as default so you have to change that. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
Discussion of swap on SSD - best not to)
[http://ubuntuforums.org/showthread.php?t=1937251](http://ubuntuforums.org/showthread.php?t=1937251)

Arch has some very good, detailed info:
Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.

UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
GUIDE: (U)EFI installation Also full install post *52 superfreak pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

There are other threads in forums with users who had issues and most have installed ok after working thru the issues.

From the UEFI menu, you should get two options to boot, one UEFI and the other BIOS/AHCI/legacy or whatever your UEFI calls it. How you boot installer determines how it will install.


For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using UEFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

---

### Post by drmrgd on 2012-08-07
I think the only real "problem" (and I quoted that since there's a number of fixes and ways to do it now....it's getting easier!) is dual booting.  Your post doesn't suggest that you're trying to dual boot, in which case setting up Ubuntu in UEFI is super simple. 

In your ASUS UEFI BIOS menu, you'll see two choices for your Ubuntu install media (USB or CD).  Be sure to choose to boot the UEFI image, or else you'll be booting in BIOS mode instead.

Also, be sure to partition your drive correctly, putting about 100 - 200 MiB as the EFI_Boot parition, and then partitioning the rest how you like.  You should be able to do this by choosing the manual partition option during the Ubuntu installation. 

In my recent build, I went with an Nvidia card, and so I can't tell you much about that.  I will say that the Nvidia card worked right out of the box once I booted up and installed nvidia-current.  Hopefully someone can tell you a little more about how to set up that card.

---

### Post by Insomniac0des on 2012-08-07
No, I am not trying to install windows, just Ubuntu.

Yea I read about it in an article when one would have to put the first 100-200 mb as the EFI_Boot, but I wasn't sure how to go about it.

@oldfred: I gave 16GB of memory, and since i hibernate, so I will probably create an equal amount of 'swap'. Yea, I also plan to mount the /home of my 2TB HDD and leave /tmp and /var/log on tmpfs and leave the rest of the ssd.

@drmrgd: Would you happen to know of a tutorial which clearly states how to proceed once you have booted in uefi mode using the Ubuntu Live CD. I mostly need the part where you create the GPT.

Thank you.

---

### Post by drmrgd on 2012-08-07
It's a lot of reading, but have a look through the links that Oldfred provided, including the top of his post.  I don't have any better links than those unfortunately. 

In Kubuntu the partition manager is a little different than I remember it being in Ubuntu, so I can't quite remember where to set each choice.  I sort of remember when you're setting up the fresh partition table there being a drop down menu that says something like MBR by default, and you want to change that to GPT.  Once you've (found and) selected that setting, the rest is as usual - partition and label as you like, making sure to put an efi_boot partition in the front.

---

### Post by oldfred on 2012-08-07
If not using Ubuntu's liveCD, you can download gparted liveCDs and use those. Often worth having anyway as an emergency boot/repairCd or USB.
In gparted, select gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Repair/partition linux liveCDs
[http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

If you are using a SSD, I do not see any advantage to hibernating?? With my BIOS system and an inexpensive "lower" speed SSD, it takes about 9 to 10 seconds from grub menu to working system. My BIOS & grub actually take longer. But if you have a large rotating drive even the 16GB for swap is not a large part of a drive.

---

### Post by Insomniac0des on 2012-08-07
@oldfred: okay, got it. So having read a lot of articles, I have the fundamental idea of where I'm headed.

So I have 2 drives, 120 GB SSD and a 2 TB SATA3 (5900 rpm).

Is it okay if I partition my ssd as primary and my HDD as a logical volume LV and mount my /home on my HDD, while I use the ssd for everything else ?


And finally, should I ditch the swap ? I didn't quite get your point.

Thanks.

---

### Post by oldfred on 2012-08-07
With a 2GB drive putting swap on it does not really use any space. With as much RAM as you have you may never use it unless you do hibernate.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

With gpt all partitions are primary. I do not use LVM and some have posted that while it has some advantages, in actual use they are small.

I see many putting /home on the hard drive, but I always install to a 25GB / (root) partition, so I have two / on my 60GB SSD. And I keep /home inside my root, but move all data to my rotating drives. I did this before with my drives as I had / in one partition and data in data partitions. I started with a NTFS partition when I was still booting XP and still have some data there, and now all new data goes into my ext3 (I would use ext4 now) partition.

```
fred@fred-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G  9.5G   17G  37% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M  1.0M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  128K  2.0G   1% /run/shm
/dev/sda1        55G   36G   20G  65% /mnt/cdrive
/dev/sdc2       100G   30G   70G  30% /mnt/shared
/dev/sdc6        97G   42G   51G  46% /mnt/data


```

```
fred@fred-Precise:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3645 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    0700  Precise
   4        58925056       117229743   27.8 GiB    0700  Quantal

```

---

### Post by Insomniac0des on 2012-08-07
Thank you for the help. Now it all makes sense. :)

---

