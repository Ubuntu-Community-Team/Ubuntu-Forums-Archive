---
title: "Ubuntu 10.10 x64 Desktop + non-mac UEFI possible?"
date: 2011-02-07
forum: Apple Hardware Users
---

### Post by Espionage724 on 2011-02-07
I've been looking for a Linux distro that:

- Works with Wine
- Has x64 support
- Can boot on UEFI systems

And Ubuntu can be ran on Mac's (which hopefully isn't only supported in legacy MBR boot) from what I read.

Fedora 14 has a EFI installer, but for some reason, my computer (no matter what disc) will not boot Fedora 14 for whatever reason (almost like there is a block on booting Fedora only or something). But I can burn some other OS to the same disc and it will work flawlessly. A USB install of Fedora will just have some kernel failure when I try to start it under UEFI.

What I have read on EFI support and Ubuntu is, I have to aparantly compile Grub2, have another copy of linux on hand, etc. I really don't wish to try this (mainly because I have bad past experience with compiling, would get to almost the last step and then have something fail compiling even though it should work, etc). So I was hoping Ubuntu would have a .efi file on the disc?

TLDR: Will a Ubuntu 10.10 Desktop x64 CD-Rom contain a working bootx64.efi that can be used on non-apple UEFI compatible systems?

---

### Post by srs5694 on 2011-02-07
First, I've successfully installed Fedora 14 in a VirtualBox environment using EFI. The key to doing so was the following (taken from my installation notes):


[list=1]
[*]Mount DVD's /images/efiboot.img file, extract /EFI/BOOT/BOOTX64.efi file, and create new DVD image with that file in DVD's /EFI/BOOT directory.
[*]Boot new DVD image using virtual machine; must use EFI's browse to file image to boot the BOOTX64.efi file, which starts GRUB.
[/list]


Basically, whoever set up the EFI boot for the CD did half the job. In theory, an alternative would be to take the /images/efiboot.img file, write it to a USB flash drive, and boot from that. I've not tried that approach, though.

I also had to compile the latest GRUB 2 from source code and muck with it to get video working correctly, but I believe that was because of issues with the VirtualBox video support, which is weak in EFI mode. Chances are it'll work better on a real system.

Second, to the best of my knowledge, Ubuntu through 10.10 provides no means to install directly in EFI mode; you've got to install using BIOS support and then modify it to boot in EFI mode. Certainly that's true of the 32-bit installer. If your motherboard has a BIOS compatibility mode, you could do it that way just to get it booted, then switch to EFI mode if you prefer. The process would be similar to what I describe [here,](http://www.rodsbooks.com/ubuntu-efi/index.html) although many of the details would differ. (You'd probably use GRUB 2 as your main boot selector, for instance, rather than rEFIt.) Alternatively, you could install everything on a BIOS-based computer, compile and set up GRUB 2 from source, and then do a hard disk transplant. (You'd need to set up the disk with a GUID Partition Table (GPT) and both an EFI System Partition and a BIOS Boot Partition, since you'd need it to boot temporarily on the BIOS-based computer and then on the EFI-based computer.)

Third, I've tested the alpha 2 of Ubuntu 11.04 in EFI mode. It includes an EFI-based installer that worked reasonably well on one system (with an Intel motherboard with UEFI boot support), a little less well on another system (using UEFI DUET; the problems were related to X video support, and so may not have been EFI-related), and not at all under VirtualBox (again, there were video issues). Thus, if you prefer Ubuntu to Fedora and have problems getting 10.10 working, the alpha 2 might be the way to go. It might be a bit flaky in the short term, though (I didn't test the installed system extensively; I was just testing the installer.) You could then upgrade to the final release in two months or so. I'm not sure if you could do a direct upgrade, though; you might need to wipe and then re-install the OS. Thus, I strongly recommend creating a separate /home partition.

---

### Post by Espionage724 on 2011-02-07
Thank you for the response. I'll start downloading the Fedora 14 DVD now and give this a try :)

As for the 11.04 EFI, when I start it, I first get a "no prefix set" error, but then it goes to the Grub menu. No matter what I select on that list, it will go to a black screen, following some CD activity, then nothing.

---

### Post by srs5694 on 2011-02-07
I suspect you've got some video problems, then; that's basically what happens on my VirtualBox tests. What sort of motherboard do you have, with what sort of video chipset? You could try, after waiting a couple of minutes, hitting Ctrl+Alt+F1 to get a text-mode prompt. If you see a text-mode shell, you can then examine the dmesg output to see if the EFI framebuffer device is being initialized and check /var/log/Xorg.0.log file to see what video driver X is trying to use. Perhaps forcing it to use another one (by deleting the driver file it's trying to use and/or installing other drivers) would help -- that's how I got the installer to work on a system with an nVidia chipset using UEFI DUET. (The nouveau drivers that were loading by default produced a garbled display, so I removed them and installed the older nv drivers instead.) Of course, you won't be able to do this if you can't get a text-mode display.

---

### Post by wbs75 on 2011-02-08
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

I found my notes and here link i follow for most part on my Mac.

---

### Post by Espionage724 on 2011-02-08
I'll try following that guide wbs75, but I'll just throw some stuff here for comfirmation.

- Install Linux with correct architecture
I have a non-mac UEFI system, so I assume it's safe to use Ubuntu 10.10 Desktop x64.

- Build GRUB 2 EFI
- I get the source, go to any ubuntu x64 computer, and compile it?
- I run the code under ```
Only for Grub trunk version (>=1.99beta)
``` then the code under ```
For models with 64-bit EFI (all non-Mac UEFI systems and >2008 Mac models), build under Linux (not MacOS X) :
``` and I assume I'll end up with some grub.efi file?

- Install GRUB
On Linux booted in BIOS mode, mount the EFI partition and create a directory :
My EFI partition = what exactly? My laptop has a HP_TOOLS volume that has some EFI diags on it, but this partition isn't needed for basic UEFI functionality. But since thats the only partition I have that's not normal, I take it I use this.

- Then, build an EFI application for GRUB and copy it and the other modules:

I run the code under ```
Grub >=1.99beta (recommended)
``` and that looks like I get the grub.efi thing?

And since my computer is UEFI, that is equal to the normal Apple bootloader right? ```
/EFI/BOOT/BOOTX64.EFI
``` is how I can boot EFI files on other OS's

And from then on I'm a bit lost :(

Isn't it at all possible to take a GRUB2 precompiled from lets say Fedora, setup the config for ubuntu, then just boot with that? 

And if I started the uBuntu installer in UEFI, will it set itself up like it should for a UEFI system? The main thing I mean here is the partition map, will it automatically put itself to GPT instead of MBR?

And if I were to somehow get Ubuntu installed while under UEFI, how would I boot it? Like with Windows 7, on my boot menu, I have an option called "Windows Boot Loader" (this is only after a UEFI install of course). If GRUB2 made an entry like this, this would be cool, I'd rather not have to select an EFI file every time to boot :/

EDIT: o and srs5694, my computer is a Compaq 515 with Radeon HD 3200 graphics.

---

### Post by wbs75 on 2011-02-08
1)  Here how i got Windows 7x64 to boot & install Rocket RAID 2310 PCIe Controller using 2 SSD w/ RAID 0. On Mac Pro Quad-Core 2x 2.7   Window has to be ACHI mode.   Im not sure if i was UEFI or not.

# Step 1	I had window 7 already install on SATA drive and made custom WIn7 x64 install disk. 1step  was formatting disk to boot UEFI.  I use this link & hti s command.

[http://www.insanelymac.com/forum/lofiversion/index.php/t184349.html](http://www.insanelymac.com/forum/lofiversion/index.php/t184349.html)

&#8220;oscdimg -w4 -os -lWin_7_x64_UEFI_ISO9660 -m -o -n -pEF -e -bd:\WIN64ISO\efi\microsoft\boot\efisys.bin d:\WIN64ISO d:\Win_7_x64_UEFI_ISO9660.iso&#8221;

# Step 2 	I use RT7 Lite 2601 Beta  to customize UEFI.ISO and  use tweak feature to set registry machi 0 

2)  Then I formatted drive in OSX as GUID.   Use Paragon to format NTSC

3) Booted UBUNTU 10.10 

- Create a small FAT32 Partition at the beginning of the drive
- I chose to make a 100mb partition and formatted it to FAT32
- This re-sized and moved my W7 partition down the drive by 100mb

4)  I use Grub files from boot.zip from this link [http://osx86.co/f74/how-to-boot-mac-pro-in-ahci-mode-t3159/](http://osx86.co/f74/how-to-boot-mac-pro-in-ahci-mode-t3159/)  and place them in the FAT32 Partiton.   Th

5)  I use variation of these commands from here [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook) 
to work with my system & disk .  I use ubuntu  istall disk and wasn&#8217;t thinking when I rebooted to save my commands.   I had to do some tweaking to get it to work  for Windows 7, base I use was this.

#  sudo mkdir /mnt/EFIDISK
# sudo mount /dev/sda1 /mnt/EFIDISK/
# sudo mkdir -p /mnt/EFIDISK/efi/grub

# cd grub-core
# ../grub-mkimage -O $EFI_ARCH-efi -d . -o grub.efi -p "" part_gpt hfsplus fat ext2 normal chain # # boot configfile linux multiboot
# sudo cp grub.efi *.mod *.lst /mnt/EFIDISK/efi/grub


6. Then I booted to OSX and install gdisk-0.6.8 2 to each drive.

7. use iPartition to write MBR code.

8. use  johnsock's script to enable ACHI mode which you can find from here.  [http://osx86.co/f74/how-to-boot-mac-pro-in-ahci-mode-t3159/](http://osx86.co/f74/how-to-boot-mac-pro-in-ahci-mode-t3159/)

9. install refit

10 unplug all my drives except Windows  RAID 0 

11.  Booted Windows 7 from Refit Menu and  install

12.  It work!!!!   


13 For Ubuntu I just follow grub install instructions and booted it from refit

---

### Post by wbs75 on 2011-02-08
refit

[IMG]http://dl.dropbox.com/u/7015415/Screen%20shot%202011-02-08%20at%206.10.06%20AM.jpg[/IMG]

Apple EFI
[IMG]http://dl.dropbox.com/u/7015415/Screen%20shot%202011-02-08%20at%206.12.05%20AM.jpg[/IMG]

---

### Post by srs5694 on 2011-02-08
> **Espionage724 said:**
> I have a non-mac UEFI system, so I assume it's safe to use Ubuntu 10.10 Desktop x64.

On (U)EFI systems, it's best to stick with an OS architecture that's the same as the (U)EFI architecture -- 64-bit in your case. If you don't, you'll lose some functionality (although I admit I'm unclear on precisely what you'll lose).

> - Install GRUB
On Linux booted in BIOS mode, mount the EFI partition and create a directory :
My EFI partition = what exactly? My laptop has a HP_TOOLS volume that has some EFI diags on it, but this partition isn't needed for basic UEFI functionality. But since thats the only partition I have that's not normal, I take it I use this.

It sounds to me like you may have a computer that's currently booting Windows in BIOS mode. If so, there's *no need and only an infinitesimal advantage* to get the system working in (U)EFI mode. In fact, doing so will be a hassle at best, and will probably render Windows unbootable. If you just want to experiment with this for the heck of it, then fine; but if you want a workable Linux installation, and especially a workable dual-boot Linux/Windows installation, you're far better off sticking with BIOS mode -- at least today (in early 2011).

To be sure of what you've got, download [GPT fdisk (gdisk)](http://sourceforge.net/projects/gptfdisk/files/) for whatever platform you can currently boot on the computer and view its output (by typing "sudo gdisk -l /dev/sda" under Linux or launching an Administrator-mode command prompt and typing "gdisk -l 0:" under Windows -- note those are lowercase Ls in "-l", not digit 1s). You'll see, among other things, something like this:

```
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present

```

This example shows a Master Boot Record (MBR) disk; note the "MBR: MBR only" and "GPT: not present" lines. If that's what you've got, you're far better off installing Linux in BIOS mode. Your computer probably boots in (U)EFI mode if you see something like this:

```
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

```

Note the "MBR: protective" and "GPT: present" lines. In this case, you should also see an EFI System Partition, identified by a partition with a type code of EF00, as in:

```
Number  Start (sector)    End (sector)  Size       Code  Name
   1             440          410039   200.0 MiB   EF00  EFI System

```

The partition number, start sector, end sector, size, and name may not match this example; just look for "EF00" under the "Code" column. That's your EFI System Partition. If you're following the instructions on the GRUB wiki, that's where you install it. If you install a Linux distribution more directly in EFI mode, the installer should detect and use the partition automatically; however, it's possible it will need some coaxing or hints, particularly if you select a manual partitioning option. In Ubuntu 11.04 alpha 2, for instance, you may need to flag the EFI System Partition as an "EFI boot partition" (I think that's what they call it, but I might not be remembering quite perfectly).

> And since my computer is UEFI, that is equal to the normal Apple bootloader right? ```
/EFI/BOOT/BOOTX64.EFI
``` is how I can boot EFI files on other OS's

That's just the name that the (U)EFI conventionally looks for by default to continue the boot process. If you install Windows, that file will be provided by Windows and it will boot Windows directly. If you install Linux, that file will be a renamed GRUB in .EFI form (or the Linux installer might put the file elsewhere and require you to hunt for it in the EFI's built-in boot selector; it varies from one installation to another).

> Isn't it at all possible to take a GRUB2 precompiled from lets say Fedora, setup the config for ubuntu, then just boot with that?

In theory, yes. Note that Fedora doesn't use GRUB 2; it uses a hacked version of GRUB Legacy with EFI support.

> And if I started the uBuntu installer in UEFI, will it set itself up like it should for a UEFI system? The main thing I mean here is the partition map, will it automatically put itself to GPT instead of MBR?

If you're starting with a blank disk (with no partition table at all), then yes. If you start with a partition table, it might not. IIRC, the Ubuntu installer didn't automatically convert to GPT even with a blank (but existing) MBR partition table. If you've got GPT to start with, you're fine, provided you've got an EFI System Partition on the disk.

Also, note that most tools that convert from MBR to GPT do so destructively -- you lose all your partitions. It's possible to convert existing partitions non-destructively with gdisk, but Windows won't boot afterwards. There's a long procedure [here](http://www.insanelymac.com/forum/index.php?showtopic=186440) for changing Windows to boot from BIOS to (U)EFI, but I've never tried it -- at least, not successfully.

> And if I were to somehow get Ubuntu installed while under UEFI, how would I boot it? Like with Windows 7, on my boot menu, I have an option called "Windows Boot Loader" (this is only after a UEFI install of course). If GRUB2 made an entry like this, this would be cool, I'd rather not have to select an EFI file every time to boot :/

This varies from one (U)EFI and Linux distribution to another. There's probably an option in your (U)EFI to select a boot file and add it to the (U)EFI's own boot menu. Depending on how the Linux installer sets up GRUB 2 (or whatever boot loader it uses), you might end up with GRUB 2 replacing your Windows boot loader, in which case the system will boot straight to GRUB, and from there to Linux. You might then need to reconfigure GRUB to get it to boot Windows. My (very limited) testing with this suggests that the current GRUB OS detection scripts in Ubuntu don't do a good job of rendering Windows bootable from GRUB 2.

---

### Post by Espionage724 on 2011-02-08
Na my computer boots windows currently in UEFI, and I notice that WIndows creates an invisible EFI partition also. My Map scheme is in GPT too.

I don't wish to keep windows on here at all, so if having Ubuntu + UEFI means loosing everything, I'm fine with that :)

I'll do some more reseach into UEFI booting and Ubuntu, but could someone please link or upload their grubx64.efi file?

---

### Post by srs5694 on 2011-02-09
I've just uploaded an entire GRUB 2 configuration to [http://www.rodsbooks.com/grub-efi.tgz](http://www.rodsbooks.com/grub-efi.tgz). Note that's a download link for a tarball. Extract it in the root of your EFI System Partition and it will create or overwrite your EFI/BOOT directory in that partition. This includes a BOOTX64.EFI file, which holds the GRUB boot-time binary, as well as GRUB module files and a grub.cfg file -- essentially, everything that's normally in /boot/grub. I built this from scratch using the stock [GRUB 1.99-rc1](ftp://alpha.gnu.org/gnu/grub/). This installation looks to the EFI System Partition's EFI/BOOT directory for the files that ordinarily go in /boot/grub, so you'll have to manually update grub.cfg in EFI/BOOT whenever you upgrade your kernel or otherwise want to make changes. Of course, you'll need to create your own grub.cfg file from the outset; the one included in the tarball will almost certainly not work for you.

---

