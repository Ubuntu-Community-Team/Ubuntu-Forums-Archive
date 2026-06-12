---
title: "Can't get ubuntu to autodetect my Sandisk Sansa E280"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by mrgod on 2007-05-27
Hi :)

I'm running Ubuntu 7.04, with Gnome. My goal is to mount the Sandisk Sansa E280 mp3-player as a normal disk mount and get Amarok to connect to the player. I can't get any of those to work :(

I have tried both MSC and MTP on my mp3-player, but there is no detection at all when I connect the player. I got an USB-HDD and ubuntu detects that one perfectly. I have also tried an another USB-port, but no detection happened.

lsusb shows:
Bus 003 Device 004: ID 0781:7421 SanDisk Corp. 
Bus 003 Device 003: ID 152d:2338  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c03f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

dmesg shows:
[ 6253.056461] usb 3-4: new high speed USB device using ehci_hcd and address 4
[ 6255.910920] usb 3-4: device descriptor read/64, error -110
[ 6261.144037] usb 3-4: unable to read config index 0 descriptor/start
[ 6261.144047] usb 3-4: chopping to 0 config(s)
[ 6271.138544] usb 3-4: string descriptor 0 read error: -110
[ 6281.132925] usb 3-4: string descriptor 0 read error: -110
[ 6291.127431] usb 3-4: string descriptor 0 read error: -110
[ 6291.127556] usb 3-4: no configuration chosen from 0 choices

As you see, the Sandisk is there, but the autodetect seems to fail...

Thanx for all help ! :)

---

### Post by NewJack on 2007-07-27
Try this HowTo:

[http://ubuntuforums.org/showthread.php?t=312196&highlight=sansa](http://ubuntuforums.org/showthread.php?t=312196&highlight=sansa)

I am planning to pick up a E280 myself and looks like this guy got most of the Sansa stuff figured out.

Please let me know if it worked.  Thanks!  Good Luck!

---

### Post by sharperguy on 2008-05-28
[http://ubuntuforums.org/showpost.php?p=3798461&postcount=118](http://ubuntuforums.org/showpost.php?p=3798461&postcount=118) might help you if you still haven't fixed it.

---

