---
title: "Problem dual booting xubuntu with mac OS"
date: 2019-02-04
forum: Apple Hardware Users
---

### Post by cyber.cypress on 2019-02-04
[FONT=verdana]Hi everyone, hope you might be able to help me.[/FONT]
[FONT=verdana]I recently tried to set up a dual boot with xubunutu 18.04.1 on my macbook air. I created a partition on my SSD and set up rEFInd as a bootloader.

[/FONT]
[FONT=verdana]I used a live USB to boot into xubuntu to test everything out first, and everything seemed to be running smooth. I went through the process of installing xubunutu, choosing the "something else" option. I set up a swap partition, then a Ext4 journaling file system with a mount point of /, and finally chose the ext4 partition for the bootloader installation.

[/FONT]
[FONT=verdana]After the installation completed, I restarted the computer. I was able to select which OS to boot after restart, but when I select ubuntu all I get is a black screen with a blinking underscore cursor, and cannot type anything or access any menus. I can still boot into the mac OS with no problems. I have tried running through the installation again, but it has not changed anything. Anyone know what is going on?  

[/FONT]
[FONT=verdana]My specs are: 2014 MacBook Air 
Intel Core i5 1.4 ghz processor
 8GB RAM 
Intel HD Graphics 5000 1536 MB

[/FONT]
[FONT=verdana]Any advice or suggestions would be much appreciated, thank you![/FONT]

---

### Post by yancek on 2019-02-05
> [FONT=verdana]and finally chose the ext4 partition for the bootloader installation.
[/FONT]

If you are using rEfind as the bootloader, this would be an EFI install and your Xubuntu boot files should be on an EFI partition not the / partition.  You could boot the Xubuntu install usb and check to see what partitions you have and if there is an EFI partition, mount it and take a look at it to see if you have any ubuntu directories/files on it.

---

### Post by oldfred on 2019-02-05
Moved to Apple hardware sub-forum, so those with Mac will see it.

See also:
[https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640](https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640)

---

### Post by cyber.cypress on 2019-02-05
Thanks for your suggestion!  That makes sense and I thought for sure it would work, but I still get the same thing when I choose the EFI partition for bootloader installation.  

When running from the install usb I can see the EFI partition when I look in GParted, but can't mount it to look at the contents.  It says 29 MB are used up in the partition, but I can't tell what it is.  The file system for the EFI system partition is fat32, and it lists flags as boot, esp

---

### Post by oldfred on 2019-02-05
Do not know Mac and any unique issues it may have.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cyber.cypress on 2019-02-05
here is the report it generated.  the top says no boot loader is installed, but rEFInd is working whenever I start up the computer...

[http://paste.ubuntu.com/p/TqW4yJBjSr/](http://paste.ubuntu.com/p/TqW4yJBjSr/)

---

### Post by oldfred on 2019-02-05
You do not want anything in MBR as that is only for BIOS boot. With UEFI the MBR is empty.
But it looks like at some point you installed a BIOS boot version of grub and installed its boot loader to the PBR - partition boot sector of the ESP.
And since you do not have the mount of the ESP- efi system partition in fstab, you must have installed the BIOS version of grub.
You can boot Ubuntu live installer in UEFI mode, and install Boot-Repair. Then in advanced mode uninstall grub-pc(BIOS) and install grub-efi-amd64 for UEFI boot.

You also seem to show hybrid partitioning which is both MBR and gpt. The MBR is just for the first 4  primary partitions and used to be used on old Mac to boot Windows before Windows had UEFI, but Mac was already UEFI.
If you get hybrid out of sync, it can cause major partition issues.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
convert hybrid to protective MBR gdisk experts commands  p, x, n, p, w
[http://askubuntu.com/questions/650194/repair-windows-boot-loader-after-installing-ubuntu-on-macbook-pro](http://askubuntu.com/questions/650194/repair-windows-boot-loader-after-installing-ubuntu-on-macbook-pro)

---

### Post by cyber.cypress on 2019-02-06
That seemed to have worked!  Thank you so much for your help!

---

