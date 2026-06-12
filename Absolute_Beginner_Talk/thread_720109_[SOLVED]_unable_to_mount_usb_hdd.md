---
title: "[SOLVED] unable to mount usb hdd"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by rabbit2502 on 2008-03-09
:confused: OK, I've been searching the post for a couple of days for something that might help but not sure what to do.

I have a Dell Inspiron 531s desktop AMD Sempron 3600+ 2.0 ghz, 512mb 667mhz ddr2, and 

nVidia geforce6100 nForce 430. It has a 80gb hdd with Vista. and I'm running UBUNTU from 

a 120 gb wd usb hdd. My problem is when I first set up the system everything worked fine 

but now I'm unable to access my 2nd usb hdd it's also wd 160gb it was formated with 

winxp and used for file storage on another system I had it has photo, music, and such on 

it. I want to transfer my photos and music to UBUNTU, but when I turn the drive on I get an 

error message see attached screen shots for message and contents of ect/fstab.

---

### Post by Tatty on 2008-03-09
This happens sometimes if you do not unmount a device properly in windows before disconnecting.

Did you try following the device in the error message?

---

### Post by jepong on 2008-03-10
what happened if you try to type "lsusb" in the terminal?

I got my P990i connected in USB mode using this.

---

### Post by rabbit2502 on 2008-03-10
this is what I've tried so far. Shut down Ubuntu tried to restart with 2nd hdd connected and powered up, Grub error 22 on boot. Shut down system turned off 1st & 2nd usb drives. Grub error 17 Shut down again turned on 1st usb drive (UBUNTU) rebooted to windows started 2nd usb hdd checked some files play some music to make sure drive worked in windows, did safely remove hardware and shut down all usb drives. Shut down windows rebooted to UBUNTU same error. now what. It also say " On your own responsibility type on command line ect... but I haven't been able to figure out how to do this step :?:

---

### Post by swat253 on 2008-03-10
I'll be watching this thread with interest as I have just d-loaded a fresh copy of Ubuntu.

I want to install it on a 160GB USB drive and boot from there while I learn the new system!

---

### Post by rabbit2502 on 2008-03-10
lsusb
Bus 002 Device 006: ID 15e9:2100 Pacific Digital Corp. 
Bus 002 Device 005: ID 1058:0404 Western Digital Technologies, Inc. 
Bus 002 Device 004: ID 067b:2507 Prolific Technology, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. 
Bus 001 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 001 Device 001: ID 0000:0000  
these are what is on usb, keyboard, mouse, ext cd rw drive = device 6, 2 wd usb hdds, printer.

---

### Post by rabbit2502 on 2008-03-10
that is what I did. put it on a 120 gig usb hdd used the live cd with minimum graphics. But didn't know how to configure grub resulting in having to have the ext drive runnin to boot to either os.

---

### Post by cpuobsessed on 2008-03-10
You need to reconnect the drive to a WinXP machine and run scandisk on it. It is reporting that the drive was not cleanly unmounted and may have errors on it. Probably disconnected without using the unmount device tool.

---

### Post by cpuobsessed on 2008-03-10
Let me see if I understand correctly:
[LIST=1]
[*]Windows installed on internal 80Gb
[*]Ubuntu on USB HD
[*]Other files on another USB HD
[*]Grub is installed on 1st USB HD
[/LIST]
So you have to have the 1st USB HD plugged in at boot time or else you can't boot to windows or linux

---

### Post by cpuobsessed on 2008-03-10
Vista really screws things up when you try to dual boot.

---

### Post by rabbit2502 on 2008-03-10
OK I have been able to use the drive from windows checked it for errors video files work music file play and pictures can be opened and edited. what is strang is it worked with Ubuntu when I frist installed ubuntu now it doesn't.

What is $Logfile? it indicates a bad shut down can this file be found and edited? or should I just try to force the mount and hope for the best? there are file I don't want to loose on there could that happen by forcing it to mount as suggester in the error message?

---

### Post by rabbit2502 on 2008-03-10
> **cpuobsessed said:**
> Vista really screws things up when you try to dual boot.
I didn't intend to have dual boot I was trying to set it up so it would boot from usb when i used f12 for boot menu and could choose which drive to boot from. I think I wound up with grub on the C drive with windows.

---

### Post by rabbit2502 on 2008-03-10
Not sure what I did but now it works, go figure.

---

