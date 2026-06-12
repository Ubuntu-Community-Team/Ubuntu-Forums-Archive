---
title: "Installing Ubuntu LTS (problems with GRUB install)"
date: 2017-04-13
forum: Apple Hardware Users
---

### Post by apol1 on 2017-04-13
Hello, Im attempted to re-install Ubuntu LTS 16.04 on my PC. Ive reinstalled before but suddenly im getting this error window that says:

Unable to Install GRUB in /dev/sda

Exucuting 'grub-install/dev/sda' failed

This is a Fatal Error

Attitional notes: A currupted Ubuntu OS seems to be failing format away (might be part of the trouble)

Machine Specs

[FONT=Verdana]Video Card: 4GB EVGA NVIDIA GeForce GTX970 GDDR5 video card
Ram: [/FONT]
**[FONT=Verdana]DDR4 Memory[/FONT]**
   [FONT=Verdana]32GB Crucial Ballistix DDR4-2400MHz (4 x 8GB), CAS 16 latency, low voltage

[/FONT]**[FONT=Verdana]Motherboard[/FONT]**

   [FONT=Verdana]Asus X99-A/USB 3.1 Intel X99 based chipset, ATX Motherboard

OS: UbuntuLTS 16.04
[/FONT]
I am grateful for any and all help :)

---

### Post by ajgreeny on 2017-04-13
With machine specs like that I suspect your machine is using UEFI and if so, no matter where you ask the system to install grub, it will always go to the correct site for a UEFI system, which I believe is the EFI partition on what the hardware knows as /dev/sda.

Running the boot-info script from Boot-Repair may help figure out what is going on so see **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system. 

I am not sure how that will deal with a system in a corrupt or half installed state, as yours may be, but it is worth a try.

---

### Post by apol1 on 2017-04-14
Im afraid after a night of attemtps none of these options appear possible, Im on a mac that won't format USBs to the liking of one live-USB program, and the other two require a PC and I have none to work with. Im assentially starting over from scratch so I would'nt mind formatting my hard drive completly to make a reinstall possible.

What tools would I need for that? Any other suggestions?

Thx for speedy reply BTW :)

---

### Post by ajgreeny on 2017-04-14
*Thread moved to **Apple Hardware Users**.* which is more appropriate and a better fit.

Sorry, but I can not help with Apple hardware.

---

### Post by oldfred on 2017-04-14
Are you installing/repairing a PC?
Or your Mac?

This should work if you only want UEFI install.
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

Best to install Boot-Repair using ppa into Ubuntu live installer of same version as installed.
Boot-Repair's own ISO is now getting older, based on 14.04 Lubuntu.

---

### Post by apol1 on 2017-04-15
I understand, macs from my experience are limited with this sort of thing, I might have acess to another Ubuntu machine soon, Im giving my last ditch attempt using a mac tonight.

---

### Post by apol1 on 2017-04-15
I am repairing a PC tower that has always had Ubuntu exclusive, but im using a mac as a temporary computer to repair my linux build. Unfortunatly this mac will not format anything to FAT32. Is there anything I can do to fix this or am I out of luck with this mac?

---

### Post by russkyca on 2017-04-15
Google 'how to format to fat32 on mac':
Some hits I get include:
[http://qsee.custhelp.com/app/answers/detail/a_id/2560/~/mac%3A-how-to-format-a-flash-drive-to-fat32-in-mac-os-x](http://qsee.custhelp.com/app/answers/detail/a_id/2560/~/mac%3A-how-to-format-a-flash-drive-to-fat32-in-mac-os-x)
[https://discussions.apple.com/thread/2355168?tstart=0](https://discussions.apple.com/thread/2355168?tstart=0)
[http://www.admfactory.com/how-to-format-usb-flash-drive-to-fat32-in-mac-os/](http://www.admfactory.com/how-to-format-usb-flash-drive-to-fat32-in-mac-os/)

Hope those ideas help.

---

