---
title: "Ubuntu full install on memory card"
date: 2012-09-06
forum: Apple Hardware Users
---

### Post by saadats on 2012-09-06
Hello all
I wish to install ubuntu on a memory card so that i dont change anything with my macbookair ssd and also save some space. I've been trying since a fortnight, but didn't succeed. I wouldn't like to use a live cd but have a dedicated installed ubuntu. Since my air doesn't have a cd drive, i'll use a usb drive as an installation disk. Any sort of help would really be appreciated. Thanks a lot.

Cheers
Saadat

---

### Post by Bachstelze on 2012-09-06
There are several tools you can use to create a bootable installation USB drive from an ISO. Have you done that?

---

### Post by C.S.Cameron on 2012-09-06
For a full install use an 8GB card.
Not sure what to do with a Mac, I've never touched one.
Normally I unplug the internal drive, plug in the flash drive, boot the Live CD and run install.

---

### Post by saadats on 2012-09-07
Thank you for the replies. I've tried many ways to boot but I can't find a way to install into the SD Card, since I have a macbook air, i can't disconnect the ssd, because its hardwired. What do i do now?

---

### Post by Bachstelze on 2012-09-07
Yes, you can't both boot from the SD card and then install to it. You need to use the USB port for one or the other (either use a USB stick for booting, or an USB card reader).

---

### Post by C.S.Cameron on 2012-09-07
Following is step by step how I installed 12.04 on a 8GB flash drive on an Intel machine, Not sure if this works on a Mac.
You should not require a soldering gun if you are careful about where you install grub:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.
(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system", (
And "Mount point" = /windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

### Post by saadats on 2012-09-08
Thank you Cameron, looks like a working solution. Can i install it using my windows laptop on the memory card and then use the memory card on my mac?

---

### Post by C.S.Cameron on 2012-09-08
> **saadats said:**
> Thank you Cameron, looks like a working solution. Can i install it using my windows laptop on the memory card and then use the memory card on my mac?

You should be able to install to memory card from your Windows laptop if it is fairly new.

---

### Post by saadats on 2012-09-08
> **C.S.Cameron said:**
> You should be able to install to memory card from your Windows laptop if it is fairly new.

What I'm asking is if installing on the memory card on one system (PC) lets it work if the same memory card is inserted into another system (My macbook air, in this case).

---

### Post by C.S.Cameron on 2012-09-09
> **saadats said:**
> What I'm asking is if installing on the memory card on one system (PC) lets it work if the same memory card is inserted into another system (My macbook air, in this case).

This has always worked for me between windows machines but I have never tried it on a Mac.

---

### Post by pindar on 2012-09-10
> **saadats said:**
> What I'm asking is if installing on the memory card on one system (PC) lets it work if the same memory card is inserted into another system (My macbook air, in this case).
Highly unlikely. From what I've learned in the past, for the boot sequence on the Mac, the memory card is treated like a USB drive. Macs will only boot from USB drives if they have a GPT partition scheme with a first UEFI boot partition where the bootloader is installed. I have no clue whether a PC will boot from such a card, but producing it is somewhat more complex than outlined above.

---

### Post by killtroubles on 2012-09-10
when you try to install did you see an option like " do something else " ???
i usually get 3 options with this being the last one whenever i click on install ubuntu icon and then continue option , did you ??

---

