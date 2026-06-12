---
title: "Trying to Install Ubuntu on MacBook using USB Jump Drive"
date: 2014-05-01
forum: Apple Hardware Users
---

### Post by David_Sigmon on 2014-05-01
[COLOR=#000000]I am a newbie, so I posted here instead of the Install section. I have a mid-2009 MacBook. I am trying to follow the instructions in a few Community Help Wiki documents: "Mactel Support Team / Apple Intel Installation" and "How to install Ubuntu on MacBook using USB Stick".[/COLOR]

[COLOR=#000000]I successfully downloaded ubuntu 14.04 desktop amd64.iso, and converted it to a .dmg.[/COLOR]

[COLOR=#000000]Here is my Terminal script for the next steps:[/COLOR]
[COLOR=#000000]"[/COLOR][COLOR=#000000][FONT=Menlo]diskutil list[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]/dev/disk0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#: TYPE NAME SIZE IDENTIFIER[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]0: GUID_partition_scheme *160.0 GB disk0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]1: EFI EFI 209.7 MB disk0s1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]2: Apple_HFS Untitled 94.2 GB disk0s2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]3: Apple_Boot Recovery HD 650.0 MB disk0s3[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]4: Apple_HFS Untitled 2 64.9 GB disk0s4[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/disk1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#: TYPE NAME SIZE IDENTIFIER[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]0: FDisk_partition_scheme *2.1 GB disk1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]1: Windows_NTFS Untitled 2.1 GB disk1s1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]David-Sigmons-MacBook:~ davidsigmon$ diskutil unmountDisk /dev/disk1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Unmount of all volumes on disk1 was successful[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]David-Sigmons-MacBook:~ davidsigmon$ sudo dd if=/Users/davidsigmon/Documents/ubuntu.dmg of=/dev/rdisk1 bs=1m[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Password:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]964+0 records in[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]964+0 records out[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]1010827264 bytes transferred in 193.092326 secs (5234943 bytes/sec)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]David-Sigmons-MacBook:~ davidsigmon$"

It looks successful, but I immediately get a pop-up warning: "The disk you inserted was not readable by this computer." and options "Initialize", "Ignore", and "Eject".

I have tried erasing the USB drive using the disk utility, and formatting it with FAT, and a separate time as an Apple_HFS. Each time, the computer can access it fine, until after I run the sudo function. 

I have also tried ejecting it after the successful(?) sudo, putting it back in and restarting the computer, and none of my reFit options seem to refer to the USB drive or disk1 as it is known by. If I choose the efi boot64 or grub, it says the disk cannot be found, then I get the screen where it asks if I want to Try Ubuntu, and I select it and then nothing happens for 30 minutes, so I use the power button to turn the laptop off.

Any help would be very appreciated. Thanks in advance. [/FONT][/COLOR][COLOR=#000000]I am going with the usb install, as the file won't fit on my cd-roms that only hold 800mb.[/COLOR]

---

### Post by neoanderthal on 2014-05-02
Hi there,
I just (as in earlier this week) installed Ubuntu 14.04 on my MacBook Pro 8,2, which is suffering from the discrete GPU failure that seems to be plaguing both the 15" and 17" models.
Anyhow, your steps seem all right. You might try downloading the image again if you know your hdiutil settings were correct:
hdiutil convert $ISO -format UDRW -o $DMG

The pop-up about the disk format came up for me as well, but I ignored it. After reboot the USB drive appeared in the Option-key boot list as 'EFI Disk' with the USB icon.

---

### Post by Vinodh Moodley on 2014-05-05
There is not need to convert the image. Use the ISO as is and it should work fine. I made USB installer yesterday and installed Ubuntu 14.04 and it worked perfectly. No need to convert the image.

Also, as mentioned above, ignore the "disk not readable" message and boot from the drive anyway, hold down the Option (Alt) key and select the USB "Boot EFI" option from the boot menu. There is no need to use rEFInd/rEFIt because the built-in boot menu works perfectly.

---

