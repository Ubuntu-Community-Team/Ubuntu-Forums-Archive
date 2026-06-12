---
title: "How to install Ubuntu on OSX 10.6.8 / Snow Leopard"
date: 2018-05-13
forum: Apple Hardware Users
---

### Post by pmasson on 2018-05-13
Trying to install Ubuntu on:
[LIST]
[*]MacBookPro1.1
[*]Intel Core Duo (2gHz)
[*]2GB Memory
[/LIST]

I have attempted the following on both the above machine, and on a newer MacBookAir6.2 running, OSX 10.9.5:
[LIST=1]
[*]"How to install Ubuntu on MacBook using USB Stick", 
([https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)).
[LIST]
[*]RESULT: No errors reported during this process when done on both the MacBook Pro and MacBook air, however the USB is not recognized as a bootable device when restarting the MacBook Pro: only the Mac HD icon appears when holding ALT/Option key during reboot.
[LIST]
[*]Also reviewed and followed this video covering the same process ([https://www.youtube.com/watch?v=7osgsM20Nkc](https://www.youtube.com/watch?v=7osgsM20Nkc)), again same results, USB is not recognized as a bootable device when restarting the MacBook Pro.
[/LIST]
[/LIST]

[*]Tried to create a bootable USB using UNetbootin ([http://unetbootin.github.io/](http://unetbootin.github.io/)).
[LIST]
[*]RESULT: On the MacBook Pro, could not create a bootable USB, as no USB device was listed/available in the menu items of the UNetbootin interface (although the Mac did have the USB icon on the desktop). I tried USBs formatted as both FAT32 and a Mac journaled (GUID), but neither of these were discoverable through UNetbootin.
[*]RESULT: On the MacBook Air, I could create a bootable USB through the UNetbootin interface, but again the USB was not recognized, and only the Mac HD icon appeared when holding ALT/Option key during reboot.
[/LIST]

[*]"Create a bootable stick on MacOS" ([https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0))
[LIST]
[*]RESULT: The suggested utility for creating the bootable disk, "Etcher" ([https://etcher.io/](https://etcher.io/)), will not run on the MacBook Pro.
[*]RESULT: After installing and flashing a USB stat-up disk through Etcher on the MacBook Air, again the USB was not recognized, and only the Mac HD icon appeared when holding ALT/Option key during reboot.
[*]COMMENT: The first page of instructions on the above Ubuntu tutorial state, "There are a few additional considerations when booting the USB stick on Apple hardware. This is because Apple's ‘Startup Manager', summoned by holding the Option/alt (&#8997;) key when booting, won't detect the USB stick without a specific partition table and layout. We'll cover this in a later step." However, they do not actually, "cover this in a later step."
[/LIST]
[/LIST]

Thanks for your help.

---

### Post by pquinn38 on 2018-07-30
Does anyone have a solution for the above mentioned problem.   I have macbook pro  a1150 runing 10.6, and the issues above are the same. 

Thank  you

Paul

---

### Post by shantiq on 2018-08-16
hi guys

[a small howto]("https://ubuntuforums.org/showthread.php?t=2367200&p=13670120#post13670120") I concocted to install 14.04 on a 2005 SnowLeopard Macbook
this works for me here
Have a look mayhaps

---

