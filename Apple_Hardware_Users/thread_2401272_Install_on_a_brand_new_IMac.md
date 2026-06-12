---
title: "Install on a brand new IMac"
date: 2018-09-16
forum: Apple Hardware Users
---

### Post by perran on 2018-09-16
Sorry to ask for something that probably is answered somewhere here on this giant Forum !
I searched in vain.

I want to multi boot my iMac wit Ubuntu.
OS High Sierra 10.13.6
3.4 GHz Intel Core I5
Radeon Pro 560

I am looking for a "howto" for this install.
There are a lot of info about the MacBook.
Problems during and after the installation.

I think the procedure would be something like this :
Download Unbuntu. (of course)
Use some Mac tool to create a partition, may be 150 GB
Write the Ubuntu image to a USB drive
Install some multiboot tool on the IMac
Boot up on the USB device and make an installation on the new partition
Configure the installation using USB keyboard and mouse (because the Mac wireless will not work ?)
Install drivers for the Mac keyboard and mouse. (get it where ?)
DONE (?)

I do not care if the instructions are a bit "complicated".
I have a lot of time and experience from the PC world.

All help appreciated !
Best Regards

---

### Post by oldfred on 2018-09-16
I do not know nor have a Mac. But have some links that now may not be current.
See how well Live installer works first.
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) 
    

Note that even with PC, a very new system may not have all the support required. It can take a bit before kernel is updated & drivers added or changed to support very new hardware. Sometimes those updates can be downloaded by a ppa or you have to compile yourself. Then those updates will eventually be included new distributions, depending on timing of updates & release of new version of distribution.

       [http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf](http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf)
[http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
   Install to Mac
[https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640](https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) 
   Apple's Late-2016 MacBook Pro Is Still A Wreck With Linux
[https://www.phoronix.com/scan.php?page=article&item=mbp2016-linux-wreck&num=1](https://www.phoronix.com/scan.php?page=article&item=mbp2016-linux-wreck&num=1) 
   FAT32 format  & label with boot flag on Mac
[URL="https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation"]https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation
      [/URL]
 Mac with NVMe
[http://ubuntuforums.org/showthread.php?t=2274095](http://ubuntuforums.org/showthread.php?t=2274095)
EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi) 
    [URL="https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation"]
[/URL]

---

### Post by perran on 2018-09-18
Thanks OldFred !
I am very old myself, started RedHat round 25 years ago (PC of course) !
I will check out these links.

Regards
   OldPerran

---

