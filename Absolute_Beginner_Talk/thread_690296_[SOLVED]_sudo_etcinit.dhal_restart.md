---
title: "[SOLVED] sudo /etc/init.d/hal restart"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-02-07
Hi, I've finally got my Seagate external hard drive working, but I can only access it when I type (in terminal) sudo /etc/init.d/hal restart .  I've posted elsewhere concerning the mounting process, but how do I get the terminal to reset hal each time to recognise my external hard drive?  Is there a code line I can input?  Or do I simply have to input this each time I wish to mount the device?  Thanks.

---

### Post by Pelham123 on 2008-02-08
Is the drive plugged in all the time, or is it hotplugged? If the drive is hotplugged, make sure drive is unplugged, then try this command in a terminal and then plug in drive...

lshal --monitor

Post reply?

---

### Post by Berean on 2008-02-09
I did as you suggested, but all I got was the following message, and when I hotplugged the external hard drive it wasn't recognised.

Start monitoring devicelist:
-------------------------------------------------
09:28:28.639: usb_device_bc2_3000_____________9QE2NG89 added
09:28:29.011: usb_device_bc2_3000_____________9QE2NG89_if0 added
09:28:29.071: usb_device_bc2_3000_____________9QE2NG89_usbraw added
09:28:36.686: usb_device_bc2_3000_____________9QE2NG89_if0_scsi_host added
09:28:36.686: usb_device_bc2_3000_____________9QE2NG89_if0_scsi_host_scsi_device_lun0 added
09:28:41.107: usb_device_bc2_3000_____________9QE2NG89_if0_scsi_host_scsi_device_lun0_scsi_generic added

If I enter sudo /et/init.d/hal restart the drive is instantly recognised!  Any ideas?  Your help is appreciated, thank you.

---

### Post by Pelham123 on 2008-02-09
What happens if you use another device  (ie - USB flash drive/printer CDROM etc) into new reboot of ubuntu before you plug USB drive in? Do they work? Just trying to see if your Seagate USB drive somehow turns off Hal or hal is stopped post boot. You can check if hal is up and running...

pelham123@pel1:~$ ps aux | grep hal
107       5939  0.1  0.2   5652  3800 ?        Ss   16:08   0:00 /usr/sbin/hald
root      5940  0.0  0.0   3096  1040 ?        S    16:08   0:00 hald-runner
107       5974  0.0  0.0   2160   896 ?        S    16:08   0:00 hald-addon-keyboard: listening on /dev/input/event1
root      5976  0.0  0.0   3156   980 ?        S    16:08   0:00 /usr/lib/hal/hald-addon-cpufreq
107       5977  0.0  0.0   2160   896 ?        S    16:08   0:00 /usr/lib/hal/hald-addon-acpi
107       6086  0.0  0.0   3260  1228 ?        S    16:08   0:00 hald-addon-storage: polling /dev/hda (every 2 sec)
107       6109  0.0  0.0   3260  1184 ?        S    16:08   0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
pelham123 6241  0.0  0.0   2988   764 pts/0    R+   16:13   0:00 grep hal


Hal is not running...

pelham123@pel1:~$ ps aux | grep hal

pelham123 6261  0.0  0.0   2988   768 pts/0    R+   16:13   0:00 grep hal


You could try the above command when the drive is plugged in and see what the output is. You could also try the following commands with drive plugged in 'lsusb' and 'tail | dmesg' and see if that helps...

I also tried looking for Hal entries in the system logs, but only found some in the <debug> logs. Dont really know what to suggest, just trying to help pinpoint; If Hal is turned off and whats turned it off and when..

Of course I may well be complicating the matter, when sometimes the easy solution cant be seen for looking.

Good luck :/

---

