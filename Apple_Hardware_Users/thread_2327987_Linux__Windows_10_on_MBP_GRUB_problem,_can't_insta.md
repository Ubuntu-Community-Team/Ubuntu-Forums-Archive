---
title: "Linux /// Windows 10 on MBP GRUB problem, can't install fresh OS"
date: 2016-06-16
forum: Apple Hardware Users
---

### Post by fin97222 on 2016-06-16
[COLOR=#2C2C2C][FONT=Verdana]Hi,[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]I installed Windows 10 as bootcamp. Then formatted OS X.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]Then I installed Ubuntu 14.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]When I turn on the MBP, I click alt and select which drive (usb,hard drive,etc) to startup <- That is Mac's version.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]I tried burning Windows and other Linux OS to a disc, and when I select to boot up from the USB from the selection menu, it just starts up the GRUB selection menu.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]On the GRUB selection menu there is:[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]Windows 10[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]Ubuntu[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]or I can press [C] to enter commond line.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]I formatted usb's and used rufus onto usb sticks (windows 10/7/linux but AFTER I select the usb it just log's onto GRUB it just gives me choice of windows 10 or ubuntu[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana][IMG]https://www.tekrevue.com/wp-content/uploads/2014/09/startup_manager.jpg[/IMG][/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]this is the menu I get after selecting a usb stick at the startup selector... grub does not show any usb !![/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana][IMG]http://www.howtogeek.com/wp-content/uploads/2010/05/620x412xsshot169.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.paF5jeRgbM.png[/IMG][/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]Any time I try to boot up a install it just logs onto the GRUB menu.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]how can I remove grub as default or how can I install Windows XP or 7 ontop of Windows 10[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]MACBOOK PRO,2011.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]-------------------------------------[/FONT][/COLOR]

---

### Post by oldfred on 2016-06-16
I do not know Mac.
But if you want Windows 7 you need to convert it to UEFI boot, by copying from DVD to flash drive and move files to make it UEFI bootable.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

This is more for PC:
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
       Some Mac links:
 [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
   Mac with NVMe
[http://ubuntuforums.org/showthread.php?t=2274095](http://ubuntuforums.org/showthread.php?t=2274095)
EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

