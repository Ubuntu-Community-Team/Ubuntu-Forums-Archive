---
title: "iMac(2008)/MacBook Pro(2011) boot Ubuntu from USB"
date: 2017-07-31
forum: Apple Hardware Users
---

### Post by jemibu on 2017-07-31
I've been working on trying to boot my two Apple computers from a USB drive with full Ubuntu installed. _Not_ a live installation. A full installation.

I'll preface my steps by first stating that I have this working peachy on a Lenovo X1 Carbon. I plug in the USB and it boots to Ubuntu. I unplug the USB and it boots to Win10. I'm just having an issue getting the Apple computers to recognize that the USB is a bootable device. All I see are my Windows and Mac partitions when I hold down the option key at startup. All of the forum posts I've found are for an installation on a hard drive partition. I assumed the instructions would be transferable but I'm not having any luck.

-I put Ubuntu live image onto my 4GB USB 3.0 drive using Rufus on the Lenovo
-I booted the Mac to this live image and ran the Startup Disk Creator on my 64GB USB 3.0 drive
-I rebooted and it didn't show up as a startup device. So I put it in the Lenovo and was able to boot to Ubuntu. I thought I was crazy so I did these steps again with the same results
-So I booted the USB on the Lenovo for troubleshooting
-After reading more about EFI boot here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) I created a separate partition on the drive using GParted.
-I then ran through the instructions to convert to UEFI boot with Boot Repair and installed GRUB on both partitions of the drive
-Still no luck with the Mac recognizing the drive as bootable so I try the steps again with no change.
-Installation still says Legacy Mode with ```
[ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode" 
```

Here is the summary from my Boot Repair report (can include full report as attachment by request) :
```
============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sdb2 
                       and looks at sector 13303624 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt2)/boot/grub. It also embeds following 
                       components:
                       
                       modules
                       -------------------------------------------------------
                       fshelp ext2 part_gpt biosdisk
                       -------------------------------------------------------
    Operating System:  Ubuntu 16.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img
```

The next idea is to either a) install reFind ([http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/)) onto the Mac, or b) try these instructions [https://askubuntu.com/questions/826943/booting-ubuntu-on-mac-from-usb](https://askubuntu.com/questions/826943/booting-ubuntu-on-mac-from-usb)

I'd appreciate any additional ideas. I'm new to the Ubuntu community but have found a lot of great resources so far. Thanks!

---

### Post by jemibu on 2017-07-31
Quick note: sdb1 is a 200mb partiiton bios_grub flag, sdb2 is the Ubuntu install with boot, esp flags

---

### Post by finny388 on 2017-08-04
When I use Option I see EFI Boot or something like that with EFI that represents my kingston usb drive.

the `C`key is supposed to give you the boot screen for all drives. Won`t work for me but it`s supposed to.

---

### Post by jemibu on 2017-09-08
I worked this issue from a few angles and ended up using this solution. This individual created very clear and concise instrcutions:
> [https://coljac.net/2014/stuff/installing-ubuntu-onto-a-bootable-usb-stick-or-other-device-on-a-mac/](https://coljac.net/2014/stuff/installing-ubuntu-onto-a-bootable-usb-stick-or-other-device-on-a-mac/)

You end up with a USB drive with 4 partitions:

[LIST]
[*]A 200 MB EFI Boot partition
[*]A swap partition
[*]A 200 MB ext2 partition mounted to /boot
[*]A main partition mounted to /
[/LIST]

Then you install rEFInd onto the EFI partition.

When you boot the mac with the USB attached you see the EFI partition show up as an option. Upon selecting that, rEFInd starts and you can select the Ubuntu partition to boot to.

In case the above link stops working, here are the instructions for posterity:
> [COLOR=#555555][FONT=Verdana]I recently had a reason to want to boot Linux on my Mac which already has a Windows Bootcamp partition. I wanted to just install Ubuntu onto a USB stick or hard drive and boot from that. The first bit turned out to be easy, but getting it to boot was quite arcane. I found lots of conflicting information on the web, and even after drinking from [this fire hose of useful information]("http://www.rodsbooks.com/ubuntu-efi/") it took a lot of trial and error to get it working.[/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]It is possible – you just have to install like normal but requires a third-party boot loader and bit of jiggling before it will boot on its own. I’ve documented what I did below for posterity and others beating their head against the same issue.[/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]1. First, make a bootable Ubunutu install disk:[/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana][http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)[/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]2. Boot, and by holding down the option key, get the boot menu. Ubuntu will show up as “EFI Boot” – boot that. Begin the installation.[/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana] [[IMG]http://coljac.net/wp-content/uploads/2014/09/install.png[/IMG]]("http://coljac.net/wp-content/uploads/2014/09/install.png")[URL="http://coljac.net/wp-content/uploads/2014/09/diskutil.png"]
[/URL][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]3. When you get to the installation type, pick “Something else”.[/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana][[IMG]http://coljac.net/wp-content/uploads/2014/09/something.png[/IMG]]("http://coljac.net/wp-content/uploads/2014/09/something.png")[/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]4. Find your USB disk from the list. Look at “Device for boot loader installation” down below, it will probably show the device with a readable name so you can be sure – for instance: “/dev/sdd   SanDisk Cruzer 32.0 GB”. Select this device.[/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana][IMG]http://coljac.net/wp-content/uploads/2014/09/device.png[/IMG][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**Note: My screenshots are from a virtual machine, yours will probably have the Mac’s internal HDD listed (for instance, /dev/sda, /dev/sdb) and all its myriad partitions. You want to be careful not to mess with those. **[/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**5. Now let’s partition the USB disk. Find the device above, and select “New Partition Table”. This will replace the existing partition or partitions with “Free space”.**[/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**6. Create the following partitions with the “+” button:**[/FONT][/COLOR]

[LIST]
[*]**A 200 MB EFI Boot partition**
[*]**A swap partition (optional: depending on your RAM and whether it’s a USB flash drive or hard drive). Twice your RAM up to a maximum of 8GB is recommended. On a flash drive, may wear the drive out faster.**
[*]**A 200 MB ext2 partition, mounted to /boot**
[*]**A main partition with at least 6 GB, file system ext4 (or your choice), mount to /**
[/LIST]
[COLOR=#555555][FONT=Verdana]**[B]Note 1: You can add extra partitions if you like. For instance, a FAT32 partition for sharing with the Mac. I also don’t know if c) is necessary, more experimentation required.)**[/B][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**[B][B]Note 2:  I believe the option to add an EFI boot partition is only present when you booted the installer via EFI (which is going to be the case for your Mac).**[/B][/B][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**[B][B][IMG]http://coljac.net/wp-content/uploads/2014/09/partition.png[/IMG]**[/B][/B][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**[B][B]7. Hit “install now” and complete the installation.  Afterwards, it will prompt you to reboot. Come back to OS X.**[/B][/B][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**[B][B]8. [Get gdisk]("http://sourceforge.net/projects/gptfdisk/files/") and run the .pkg installer.**[/B][/B][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**[B][B]9. Get rEFInd as a “binary zip file” [from the rEFInd page]("http://www.rodsbooks.com/refind/getting.html") and unzip it somewhere.**[/B][/B][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**[B][B]10. Open Terminal, and go to the refind-bin-0.x.x directory.**[/B][/B][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**[B][B]Type: [B]diskutil list**[/B][/B][/B][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**[B][B]Note the device that’s your USB, and the EFI boot partition. In this example, /dev/disk3 is the USB stick and /dev/disk3s1 is the EFI partition.**[/B][/B][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**[B][B][IMG]http://coljac.net/wp-content/uploads/2014/09/diskutil.png[/IMG]**[/B][/B][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**[B][B]11. type [B]sudo gdisk /dev/disk3****  (or whichever number is appropriate)**[/B][/B][/B][/FONT][/COLOR]

[LIST]
[*]**[B][B]Type: [B]x  ****(enter)**[/B][/B][/B]
[*]**[B][B]Type: [B]o  ****(enter)**[/B][/B][/B]
[/LIST]
[COLOR=#555555][FONT=Verdana]**[B][B]You’ll see one ore more MBR partitions.**[/B][/B][/FONT][/COLOR]

[LIST]
[*]**[B][B]Type: [B]n  ****(enter)**[/B][/B][/B]
[*]**[B][B]Type: [B]o  ****(enter)**[/B][/B][/B]
[/LIST]
[COLOR=#555555][FONT=Verdana]**[B][B]Now there will be one MBR partition.**[/B][/B][/FONT][/COLOR]

[LIST]
[*]**[B][B]Type: [B]w  ****(enter) to save your changes.**[/B][/B][/B]
[/LIST]
[COLOR=#555555][FONT=Verdana]**[B][B]11. In the rEFInd directory, run the installer script and point it at your EFI partition.**[/B][/B][/FONT][/COLOR]
**[B][B][B] sudo ./install.sh --usedefault /dev/disk3s1**[/B][/B][/B][COLOR=#555555][FONT=Verdana]**[B][B](or whichever disk is appropriate)**[/B][/B][/FONT][/COLOR]
[COLOR=#555555][FONT=Verdana]**[B][B]12. You should now be able to reboot with your USB device plugged in. After holding down option you should see an “EFI Boot” option. When selected, it will boot rEFInd. Alongside OS X and anything else you already have installed, there should be an option for linux/GRUB. Choose that and away you go!**[/B][/B][/FONT][/COLOR]


---

