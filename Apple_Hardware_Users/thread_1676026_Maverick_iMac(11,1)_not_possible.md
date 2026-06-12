---
title: "Maverick? iMac(11,1) not possible?"
date: 2011-01-26
forum: Apple Hardware Users
---

### Post by Lifeis on 2011-01-26
Hey guys,
So basically, I have one machine in my house which doesn't run Linux, and that is a new iMac (a few months old). It has 4GB DDR3 Ram, an intel core i3 chip @ 3.06GHz, and a ATI Radeon HD 4670 graphics card.
I want to dual boot Ubuntu (I have a disk with Maverick on it).
But I have read the wiki and I dont really understand alot of it. Right at the beginning, it says:
"This information will not work for iMac (11,1) users and recent versions of Ubuntu (e.g., Maverick). The presence of the bios-grub partition that the Ubuntu installer creates by default (e.g., sda3) causes a conflict that prevents syncing the GPT and MBR partition tables."

Does this mean that I can't dual boot Maverick? What does it mean by 'iMac(11,1)'? This iMac was bought a few months back.

Thanks in advance for all your help guys, this community is one of the main reasons why I always choose Ubuntu. Long live Ubuntu!

-Lifeis

---

### Post by arabis on 2011-01-27
I have an Imac 11.2, and I have installed Ubuntu successfully but it is not easy. I suggest you read the forum about installation stories. And you must understand all the process before going into that.

---

### Post by Colin Rovis on 2011-03-09
You say, you have installed Maverick on your iMac? 
I wonder how you did ist? Ubuntu does not recognize your 4-core-cpu, does it? 
I also have installed Ubuntu, and it is working fine, but it only recognizes 1 Core, and this IS a problem indeed!
ss
Colin

---

### Post by entangled on 2011-03-10
I'm with arabis. I have installed Maverick on a second partition my iMac (11,2) but it was far from straightforward, mainly because the ATI video is hard to set up for X (it chooses the wrong display port and sometimes gets resolution wrong). Initially I found that rEFIt would not pick up grub boot, but this is OK now (grub update I think). 
I would be surprised if Colin R found no problem with maverick install.

Whether Ubuntu uses one or four cores, permanently or on-demand, is not my concern since I'm not trying to stress the machine with parallel processes.

Ubuntu runs well on the iMac, after the setup problems.

---

### Post by beatskobe on 2011-03-10
**e** 			 			 			 		   		 		 		Was there anything else you did? I've followed all of these steps and it doesn't seem to be working...

---

### Post by Colin Rovis on 2011-03-10
Hmmm.
I got Maverick working on my 11,1 -- graphics are ok, all seems to work except the 4 cores, which are important, because Ubuntu stresses the one core a lot with nothing to do. One can load a driver for ATI. For recognizing the 4 cores Ubuntu must be started out of grub-efi, but that I could not accomplish...

---

### Post by entangled on 2011-03-10
I haven't considered before which cores are detected or being used on this system.

I have iMac 21.5" screen, i3 540 processor.

OSX 10.6 (latest update) - in Activity Monitor - shows two cores and each gets used at times.

Ubuntu 10.10 (Maverick) - in System Monitor - shows four cores and each gets used at times.

Not sure how to explain your finding - that Ubuntu uses only one core - unless there is a more reliable way to tell?

---

### Post by Colin Rovis on 2011-03-11
Hm, I have an iMac 27" (4 Cores, i7)
System Monitor shows: 1 Core.
What Istallation-Tutorial did you use?
Do you use efi-grub, and how do you start from efi-grub? (There are some tutorials which show how to install it)
I have installed the efi-grub but cannot boot out of it (it simply boots into the grub-shell. I can specify the root-entry, but not the vmlinuz-entry. The grub-shell says: there is no such partition.
I tried all possible partitions...
Ubuntu does afaik not recognize more than 1 core unless bootet out of grub-efi.

---

### Post by entangled on 2011-03-11
Colin R ...
Trying to remember what I did...and looking at some old installation CDs.
On reflection I was probably just lucky to end up right.

I used the 10.10 alternate AMD64-Mac boot disk. Attempts with the normal x86 live disk had failed to get anything showing on screen.

I have 'grub-pc' installed, now at version 1.98+20100804-5ubuntu3. I understand this is a flavour of grub-efi for PC-BIOS interface (maybe this worked because the BIOS interface was activated - somehow - Boot Camp? See below). grub-efi-amd64 is probably the more normal version on a Mac disk.

I downloaded and installed ATI Radeon driver 10.11. I think I switched to the repository version when it didn't work but then switched back to the ATI driver and it did work, but only after a reboot (or two).
 
The disk has a GUID partition table (GPT).

Mac OSX Disk Utility shows disk partitioned for Boot Camp (probably where grub-pc comes in) and the ubuntu partition as MSDOS FAT. Ubuntu sees it as ext4 (it is, but OSX has a fairly limited view of filesystems).
I think I originally created the partition in OSX with this type.

Hope you find enough clues to get your system running properly.

---

### Post by srs5694 on 2011-03-11
> **entangled said:**
> I have 'grub-pc' installed, now at version 1.98+20100804-5ubuntu3. I understand this is a flavour of grub-efi for PC-BIOS interface (maybe this worked because the BIOS interface was activated - somehow - Boot Camp? See below). grub-efi-amd64 is probably the more normal version on a Mac disk.

The Ubuntu grub-pc package is GRUB for BIOS-based computers. It's the default version of GRUB with Ubuntu.

The grub-efi package installs either grub-efi-i386 or grub-efi-amd64, depending on the platform. In either case, this is GRUB for EFI-based computers.

On an Intel-based Mac, grub-pc usually works, but only if the computer has a hybrid MBR (more on that shortly), which activates the Mac's BIOS emulation mode. It's possible to replace grub-pc with grub-efi to support booting Linux in EFI mode on a Mac. This has advantages and disadvantages over BIOS booting. I've got [a Web page on this topic.](http://www.rodsbooks.com/ubuntu-efi/index.html) If a triple-boot (OS X/Windows/Linux) system is booting fine and you're happy with it, I don't advise trying to change to grub-efi. Making such a change could make sense if you're not happy with the current configuration or if you want to reduce the potential for problems with a hybrid MBR on a dual-boot (OS X/Linux) system.

> The disk has a GUID partition table (GPT).

Mac OSX Disk Utility shows disk partitioned for Boot Camp (probably where grub-pc comes in) and the ubuntu partition as MSDOS FAT. Ubuntu sees it as ext4 (it is, but OSX has a fairly limited view of filesystems).
I think I originally created the partition in OSX with this type.

Boot Camp is a set of utilities and configurations to enable a Mac to boot Windows. This includes a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is an ugly and dangerous hack that Apple uses to get around limitations in Windows concerning booting from GPT disks on BIOS-based computers. (Recall the Mac EFI's BIOS emulation mode? It's there to enable Macs to boot Windows, since Windows doesn't support the Mac's flavor of EFI.) Linux can boot on most or all Intel-based Macs either with or without the Boot Camp features, but a typical installation relies on some Boot Camp features (namely, the BIOS emulation mode) simply because Ubuntu's EFI support is so poor.

The grub-pc package isn't really there because of Boot Camp; it's there because Ubuntu has very poor support for EFI. The 11.04 alphas are improving on that score, but I don't know how well they'd install or boot in EFI mode on most Intel-based Macs. My impression is that the EFI support in 11.04 is there mainly for a new crop of UEFI-based PCs rather than for Macs.

Part of the reason for the filesystem confusion may be a mismatch between the GPT and MBR partition tables on your system. The GPT data present the "real" partitions on the disk, and both OS X and Linux use the GPT data. Only Windows uses the MBR data, although some disk utilities in other OSes can see and modify the MBR side. It sounds like you created the hybrid MBR using Apple's utilities, which probably set up the to-be-Linux partition as FAT. When you installed Ubuntu, it probably would have ignored the MBR data, thus leaving the Ubuntu partition maked as being FAT in the MBR. That could be why it's being misidentified by Disk Utility.

If I'm right, this is technically incorrect, but I wouldn't bother changing it unless Windows is offering to format an unknown partition. In that case, Windows might be seeing the Linux partition in the MBR and thinking it's a corrupted FAT partition. This could be a recipe for disaster, and using fdisk in Linux to change the type code is in order. (Note that you must use fdisk for this; GNU Parted, GParted, and related tools will work on the GPT side, not the MBR side.) If Windows isn't offering to format the partition, then it's ignoring it, despite its being marked as FAT, and the old saying, "if it ain't broke, don't fix it" applies. It's also possible that my whole analysis is incorrect and the Linux partition isn't in your MBR. I'd need to see the output of "sudo fdisk -lu" from Linux to be sure.

---

### Post by Colin Rovis on 2011-03-12
@entangled

I did it. I installed Ubuntu exactly after the manual from srs5694 (a great description!).
It works fine (albeit with only 1 core working), unless i do not copy the grub.efi to mnt/EFI/BOOT/.
After copying the mod-files and all the other stuff into the efi-partition, Ubuntu boots into the grub-shell, and there i cannot find the vmlinuz.
i can specify the root and so on, but when I try to set the path to the vmlinuz-kernel, I always get the error-message "no such partition".
Maybe this is the cause Ubuntu does not recognize my 4-core i7, and thats very annoying...

Colin

---

### Post by Colin Rovis on 2011-04-08
I ultimately found the solution:

Just append "noapic" -- and iMac shows 8 cores ):P

---

