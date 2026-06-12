---
title: "Preparing to install Linux Mint onto Windows 7 64"
date: 2012-09-28
forum: Any Other OS
---

### Post by mantisdolphin on 2012-09-28
Hi, 

[background]
I'm getting a new 1T hdd on my so-so gaming rig because I am tired of Win7's getting malwared and slow.  

The hours spent reviewing, downloading, running "repair" and maintenance programs for Win7 is driving me to get a dual-drive system where I have one Win7 native drive and one Linux native drive.  My Linux drive will be for everyday computing and my Windows drive will be for Starcraft 2, Steam, and Netflix (unless they will work well on Linux).  

Searching the forums I find individual problems with dual-boot systems using Win7 64, but what I'd like is any advice pre-install.  Actually all the problems people report with newer systems, Windows 7, and the latest versions of Ubuntu Linux are a little worrisome .  :(

I've made a Win7 rescue CD and a Boot-Repair CD.  Just in case.

[plan]
My idea is to install the new WD Black 1T drive when it comes today and then to run a Cinnamon Mint 13 DVD to install it on that drive.

I EXPECT then to have Win7 64 on physical HDD1 (1.4TB) and Linux Mint on physical HDD2.  

That seems the simplest way to proceed.  This should work EZ-PZ, right? I'll have a no-fuss dual-boot system with no partitioning headaches.  

What I'd like to do but which seems too complicated is to put Linux on HDD1 and have Windows 7 on HDD2.  The problem is that my only back-up copy of Windows 7 is on a separate hidden partition of HDD1 (thanks to Dell).  I'd kinda like my games to run off the WD Black harddrive.  

[gratitude]
Thanks for taking the time to read this, and if you have any advice, links, or recent threads you know of covering my situation--stuff I should know--I'd really like to hear it.

[system info]
Microsoft Windows 7 Home Premium  [sucks]	
Version	6.1.7601 Service Pack 1 Build 7601	
System Manufacturer	Dell Inc. 	
System Model	Studio XPS 9100	
System Type	x64-based PC	

Processor	Intel(R) Core(TM) i7 CPU         930  @ 2.80GHz, 2801 Mhz, 4 Core(s), 8 Logical 

Installed Physical Memory (RAM)	9.00 GB	

NVIDIA GeForce GTX 560 SE	

Realtek High Definition Audio

Drive	C:	
Description	Local Fixed Disk	
Compressed	No	
File System	NTFS	
Size	1.35 TB (1,487,107,256,320 bytes)	
Free Space	887.15 GB (952,568,496,128 bytes)

---

### Post by oldfred on 2012-09-28
Moved to other OS.

Do not know about Mint, but generally it is best to keep Windows as the first drive. Older versions would not let you change, not sure about the newer ones.

Your system probably is UEFI capable. Is Windows installed in UEFI or BIOS mode. You need to have all systems installed in the same mode to have them work well. Only Ubuntu 64 bit has UEFI mode, not sure if Mint has that now or not.

If drive is gpt partitioned and first partition is efi (FAT32) then it is in UEFI mode. If first partition is just the 100MB boot/repair Windows NTFS partition then you are in BIOS/MBR mode.

I prefer to keep each drive as fully bootable on its own. That way when one drive fails you can at least boot other drive. But I copy data from one to the other as backup as well as to DVDs for archive of more important data.

You do want a smaller / (root) partition. Some with very large / partitions are having issue booting. Not sure if BIOS or grub2 bug.

If BIOS/MBR these are good, installer has not changed much. 
Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by mips on 2012-09-28
> **mantisdolphin said:**
> Hi, 

[background]
I'm getting a new 1T hdd on my so-so gaming rig because I am tired of Win7's getting malwared and slow.  

The hours spent reviewing, downloading, running "repair" and maintenance programs for Win7 is driving me to get a dual-drive system where I have one Win7 native drive and one Linux native drive.

This in my mind is user negligence. I cannot remember the last time I had a virus or malware in windows coming from xp to win7. I don't like windows and I've always had a dedicated partition for gaming and i've never had any issues wrt to virii or malware.

Do whatever you want with mint on the new hdd and when it comes to installing grub point it to the boot drive which is your win7 drive and all will be fine.

---

### Post by mantisdolphin on 2012-09-28
Thanks for the replies!  Now my problem is that my Mint DVD won't boot and neither will the Ubuntu 12.04 64.bit CD.  

I ran checksum on the Mint ISO and the Ubuntu ISO.  imgburn reported no problems burning either disk.  The Mint forums report a lot of problems installing via live DVD.  Any reports on problems installling with Ubuntu live CD on 64-bit systems?  

Should I be trying to use a different ISO, not ubuntu-12.04.1-desktop-amd64.iso but the ubuntu-12.04.1-desktop-i386.iso (since my machine is Intel and not AMD)?

When I try to boot from them the system just hangs.  I even waited 30 minutes for the Ubuntu disk to do something and it just flashed a cursor.

Any suggestions on how to boot and install a Linux system on my computer? I'm wondering if it's a UEFI problem, but I don't know how to tell if my machine is UEFI or BIOS.

Thanks!

---

### Post by oldfred on 2012-09-28
You want the 64bit version. And if UEFI only the 64 bit version offers to install in either UEFI or BIOS mode. 

You do need to know if system is in UEFI boot mode or BIOS boot mode. Most new computers offer both. And if you have Windows, then Ubuntu has to be in the same mode.

Windows only works in gpt partitioning with UEFI. So if partition table is gpt not msdos(MBR) and first partition is FAT32 and efi, then you have UEFI booting. If you just have the 100MB boot/repair and the main Windows installs with Vendor recovery & Vendor utililties partitions using all 4 primary partition then you are in MBR mode.

Post this as it will tell partition type.
 sudo parted -l

---

### Post by mantisdolphin on 2012-09-29
I'm using the 64-bit version for my 64-bit machine: Ubuntu-12.04.1-desktop-amd64.  So I should be covered whether the system is in UEFI boot mode or BIOS boot mode, right?  

Checksum was good on the downloaded ISO and imgBurn reported no problems on the burn of the ISO.

I'm not sure how to do a sudo parted within Windows.  I installed Crunchbang stable 64-bit (it doesn't look great) so I could run gparted from there.  

DISKPART in Windows has output that won't easily direct to a log file, but I was not able to determine much.  The UNIQUEID command says that it displays or sets the GPT identitifier or MBR signature of a disk. It's such a difficult-to-use partitioner that I'm afraid to mess with it too much.  ](*,) 

---------

DISKPART> list partition

Partition  1   OEM (type)   39 MB  (size) 31 KB (offset)
Partition 2 Primary		12GB	40 MB
Partition 3 Primary		1384 GB	12 GB

DISKPART> list volume

Volume 2 C OS NTFS Partition 1384 GB  Boot
Volume 1     RECOVERY NTFS Partition 12 GB System

----------

---

### Post by oldfred on 2012-09-29
I cannot tell for sure from your Windows commands, but the first partition is normally FAT32 if UEFI, so I think you are in BIOS mode.

You can run the terminal commands from the liveCD or USB. I prefer USB now as it is a bit faster, but some seem to have issues getting USB boot to work.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

