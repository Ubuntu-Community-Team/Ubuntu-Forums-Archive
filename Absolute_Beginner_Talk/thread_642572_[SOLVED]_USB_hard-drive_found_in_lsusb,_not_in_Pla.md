---
title: "[SOLVED] USB hard-drive found in lsusb, not in Places"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-12-16
I have put my former 40 gig boot drive in a USB cradle and can't access it. Gutsy booted OK and lsusb shows:

mark@Lexington-19:~$ sudo lsusb
[sudo] password for mark:
Bus 003 Device 001: ID 0000:0000  
**Bus 004 Device 004: ID 06e1:d804 ADS Technologies, Inc. **
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 13fe:1a00  
Bus 001 Device 005: ID 03eb:3301 Atmel Corp. at43301 4-port Hub
Bus 001 Device 004: ID 04b8:010f Seiko Epson Corp. Perfection 1250

BUT Place/Computer does not show the harddisk. How can I make this disk available to the currently running Gutsy OS? (I'm struggling to know how to word this question).

I have a 320 gig WORKING Gutsy. That drive, seated as Primary Master is working flawlessly. I have a former hard drive, which was Primary Master. This "old" drive is in a USB "cradle". That is, it is powered up and has a usb cable from the cradle to the "main" computer. As you can see from the lsusb, the device sees something as ADS Technologies, the maker of the cradle. 

I have turned the power to the cradle on and off a couple of times, but the drive is a no show. 

Next, from: [http://ubuntuforums.org/showthread.php?t=641719](http://ubuntuforums.org/showthread.php?t=641719)

I tried:
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb

still no USB drive available in Places or via sudo fdisk -l

Next:

mark@Lexington-19:~$ tail -F /var/log/messages
Dec 16 16:29:20 Lexington-19 kernel: [ 1409.078956] end_request: I/O error, dev sdc, sector 0
Dec 16 16:29:20 Lexington-19 kernel: [ 1409.078961] printk: 3 messages suppressed.
Dec 16 16:29:50 Lexington-19 kernel: [ 1439.108735] usb 4-3: reset high speed USB device using ehci_hcd and address 7
Dec 16 16:30:20 Lexington-19 kernel: [ 1469.271247] usb 4-3: reset high speed USB device using ehci_hcd and address 7
Dec 16 16:30:50 Lexington-19 kernel: [ 1499.433714] usb 4-3: reset high speed USB device using ehci_hcd and address 7
Dec 16 16:31:20 Lexington-19 kernel: [ 1529.596147] usb 4-3: reset high speed USB device using ehci_hcd and address 7
Dec 16 16:31:51 Lexington-19 kernel: [ 1559.758607] usb 4-3: reset high speed USB device using ehci_hcd and address 7
Dec 16 16:32:21 Lexington-19 kernel: [ 1589.921110] usb 4-3: reset high speed USB device using ehci_hcd and address 7
Dec 16 16:32:21 Lexington-19 kernel: [ 1590.053726] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Dec 16 16:32:21 Lexington-19 kernel: [ 1590.053735] end_request: I/O error, dev sdc, sector 0
^[[BDec 16 16:32:51 Lexington-19 kernel: [ 1620.083547] usb 4-3: reset high speed USB device using ehci_hcd and address 7

and this seems to be in an endless loop

So, I shut down the "main" OS and rebooted with a LiveCD. Same problem. And having the usb drive powered up at boot, locked up the boot process for both the LiveCD and the main hard drive.

Both the former boot disk (40gig - now in the usb cradle) and the current boot disk are UbuntuOS, Gutsy.

May I have a little help, please?

---

### Post by logos34 on 2007-12-16
I'd check the jumper on the back of the drive--set to 'slave' or 'CS' (cable select)

---

### Post by asmoore82 on 2007-12-16
does the cradle have it's own power source?

I think either the drive is starting to fail or is underpowered by the cradle.

---

### Post by Mark_in_Hollywood on 2007-12-16
To first response:

I'd check the jumper on the back of the drive--set to 'slave' or 'CS' (cable select)

Check

to 2nd response:

does the cradle have it's own power source?

yes, and the LED lights, I can hear the disk "spin up". No proof of course, but I tried a different hard drive in the cradle and it works.

---

### Post by logos34 on 2007-12-16
actually on second thought I had to set mine to 'master'...I remember now because I took out an internal drive that was slave (no jumper) and had to make it master so it would work with the vantec ide-usb adapter--I had to rummage around for hours looking for that damn little cap

---

