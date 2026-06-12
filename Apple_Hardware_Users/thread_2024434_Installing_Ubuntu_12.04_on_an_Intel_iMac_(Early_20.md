---
title: "Installing Ubuntu 12.04 on an Intel iMac (Early 2006, &quot;white&quot;)"
date: 2012-07-13
forum: Apple Hardware Users
---

### Post by Mildare on 2012-07-13
Hello there! My girlfriend's tired of the Mac operating system. Most software doesn't run well on the OS X 10.4. so we're ditching OS X entirely and installing Ubuntu instead. We're probably gonna go with 12.04, since it's the most recent one and the most likely to have Mac Drivers (though that may be a bit naîve). However, my experience with installing Ubuntu on Apple systems is zero. I've never done it and am worried that something might not work out-of-the-box, or at all. Could anyone help me out here? 

Dual-booting might be too much of a hassle, since she has no intention of ever going back to OS X, so we're going with Ubuntu as the sole OS, though I'm not entirely sure that's the wisest choice. 

Should I just do the regular installation with the Ubuntu Live CD, or are there additional steps required for this?

---

### Post by 2blue on 2012-07-13
About a week ago I  was all new to linux on apple too. I installed lubuntu 12.04 on an old iBook G4 from 2005. It was managable but I still struggle with some stuff like flash player and online video streams. Since you have an iMac there will likely be much less fuzz than with the powerpc build of the iBook. 

I have come as far as a laptop that boots and runs 12.04 fine, wireless works, updates went all fine, and libre office installed and runs all fine. Java runs and works with my internet based bank services.

I can play youtube videos with the firefox flash player replacer addon, but regular flash does not play well. Neither does the mplayer gecko plugin setup for firefox. I am looking for fixes and workarounds.

DVD and CD ROM work fine, and play DVDs. You should have much less issues to handle than I do.

---

### Post by yentl on 2012-07-13
Hello! I've just installed Ubuntu 12.04 in a triple boot system with OS X Snow Leopard and Windows 7.  I've not personally had any problems, except in one case,  with any applications or drivers provided with the system; they seem to work as well as their equivalents in OS X. The exception was that the graphics driver supplied by the installation outputted some random pixels to the screen before arriving at the login prompt; afterwards the driver worked fine. I assume this can be fixed if you install the nVidia proprietary driver by 
sudo apt-get install nvidia-current.
With the free driver features such as anti-aliasing and 3D acceleration may not work as well, but I've yet to encounter a case where things don't work altogether!

If you are interested in a dual boot with windows 7, as you probably know windows 7 does not support booting directly from Apple EFI (the 64 bit does with UEFI, but that's EFI 2.0 I think and Apple is still using 1.10). So you have to enable BIOS compatibility and create a hybrid partition table, which is a pseudo MBR sitting on top of a GPT partition table. I think the Mac install disc might allow you to do this by creating MBR partitions using disk utility. Otherwise, the firmware update needed for BIOS emulation comes with Bootcamp, so you could install Windows using Bootcamp and then install Ubuntu in the OS X partition. Disk Utility doesn't really work well with resizing non-OS X partitions in my experience, but you can use gparted instead.

I think there's just two things to watch out for, which is that any changes to partitioning will cause the MBR to fall out of sync with the GPT partition table. So before you leave Ubuntu after your installation, run gptsync (which also comes with rEFIt, if you prefer to use that) The other thing is that, if you are dual booting, install GRUB to the partition in which you've installed Ubuntu and not to the device; otherwise GRUB will mess up the pseudo MBR (which doesn't have an IPL space) and you may not be able to boot into Windows (when I did that, whenever I tried to boot into Windows I got back to grub, fun times).

If you are using single boot, the version of grub installed would be grub-efi. If you are dual booting with Windows, grub-pc will be installed if you are installing Ubuntu to an MBR partition, and grub-efi will be installed if you choose to install Ubuntu to a GPT partition. I'd personally recommend installing Ubuntu to an MBR partition, because I couldn't get Windows to boot properly from grub-efi even with the fakebios command. 

There's more detailed info here:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Also, you may need to bless the grub core.img file to make the firmware boot grub by default. The command will be something like 
sudo hfsbless --folder=/boot/grub --file=/boot/grub/core.img --set Boot

Good luck!

---

### Post by yentl on 2012-07-13
Hello! I've just installed Ubuntu 12.04 in a triple boot system with OS X Snow Leopard and Windows 7.  I've not personally had any problems, except in one case,  with any applications or drivers provided with the system; they seem to work as well as their equivalents in OS X. The exception was that the graphics driver supplied by the installation outputted some random pixels to the screen before arriving at the login prompt; afterwards the driver worked fine. I assume this can be fixed if you install the nVidia proprietary driver by 
sudo apt-get install nvidia-current.
With the free driver features such as anti-aliasing and 3D acceleration may not work as well, but I've yet to encounter a case where things don't work altogether!

If you are interested in a dual boot with windows 7, as you probably know windows 7 does not support booting directly from Apple EFI (the 64 bit does with UEFI, but that's EFI 2.0 I think and Apple is still using 1.1). So you have to enable BIOS emulation by creating a hybrid partition table, which is a pseudo MBR sitting on top of a GPT partition table. I think the Mac install disc might allow you to do this by creating MBR partitions using disk utility. Otherwise, the firmware update needed for BIOS emulation comes with Bootcamp, so you could install Windows using Bootcamp and then install Ubuntu in the OS X partition. Disk Utility doesn't really work well with resizing non-OS X partitions, but you can use gparted instead.

I think there's just two things to watch out for, which is that any changes to partitioning will cause the MBR to fall out of sync with the GPT partition table. So before you leave Ubuntu after your installation, run gptsync (which also comes with rEFIt, if you prefer to use that) The other thing is that, if you are dual booting, install GRUB to the partition in which you've installed Ubuntu and not to the device; otherwise GRUB will mess up the pseudo MBR (which doesn't have an IPL space) and you may not be able to boot into.

If you are using single boot, the version of grub installed would be grub-efi. If you are dual booting with Windows, grub-pc will be installed if you are installing Ubuntu to an MBR partition, and grub-efi will be installed if you choose to install Ubuntu to a GPT partition. I'd personally recommend installing Ubuntu to an MBR partition, because I couldn't get Windows to boot properly from grub-efi even with the fakebios command. 

There's more detailed info here:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Also, you may need to bless the grub core.img file to make the firmware boot grub by default. The command will be something like 
sudo hfsbless --folder=/boot/grub --file=/boot/grub/core.img --set Boot

Good luck!

---

