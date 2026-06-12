---
title: "USB/Firewire HDD"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by mistertee on 2007-08-03
Sorry if this has been answered before...but I have a USB/Firewire external HDD that I have plugged in as USB at the moment.  The first time I plugged it in Ubuntu (FF) recognized it and mounted it.  I left it plugged in and logged off since I've logged back in, it is not seen (that I can tell).  I rebooted to no avail.  Can someone give a noob a hand?

Related question, I originally tried using firewire 400, but didn't see anything happen, so a) is there a trick to getting firewire to work? and b) is firewire 800 supported (drive supports usb fw400 and fw800)?

Thanks!

---

### Post by aquavitae on 2007-08-03
I don't know much about firewire, but I might be able to help with the mounting issue.  Have you tried uplugging it and plugging it back in?  Can you post the contents of the file /etc/mtab?  It shows a list all the mounted devices.  It is possible that the drive is mounted, but not visible to you as a user.  Also, if you open a terminal and type 'lsusb' (without quotes) it should show a list of recognised usb devices attached to the system.

---

### Post by mistertee on 2007-08-03
OK just so you don't think I'm a complete idiot...I've tried pmount (the drive shows up as /dev/sda in fdisk), and it returned this:  Error: device /dev/sda is not removable.  I also tried every entry I can think of in /etc/fstab, but it always returns an error when I try to mount the drive.  Its a FAT32 drive.  A little help please.

---

### Post by mistertee on 2007-08-03
> **aquavitae said:**
> I don't know much about firewire, but I might be able to help with the mounting issue.  Have you tried uplugging it and plugging it back in?  Can you post the contents of the file /etc/mtab?  It shows a list all the mounted devices.  It is possible that the drive is mounted, but not visible to you as a user.  Also, if you open a terminal and type 'lsusb' (without quotes) it should show a list of recognised usb devices attached to the system.

Sorry you must have been posting this at the same time as my reply to myself...

Anyway, here's the /etc/mtab and yes I've tried plugging and unplugging it a couple times.

root@clayjen:/media# cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

---

### Post by mistertee on 2007-08-03
And here is the output of lsusb...not much here that I can tell.
root@clayjen:~# lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000

---

### Post by aquavitae on 2007-08-03
You're right, lsusb doesn't help.
> **mistertee said:**
> OK just so you don't think I'm a complete idiot...I've tried pmount (the drive shows up as /dev/sda in fdisk), and it returned this:  Error: device /dev/sda is not removable.  I also tried every entry I can think of in /etc/fstab, but it always returns an error when I try to mount the drive.  Its a FAT32 drive.  A little help please.
Have you tried manually mounting it using ```
sudo mount -v /dev/sda1 /media/disk
```Not implying you're an idiot here :) but its better to check rather than just assume!  Also, does the device /dev/sda actually exist (i.e. in the /dev directory)?

---

### Post by mistertee on 2007-08-03
Thanks for the help aquavitae.  I figured it out.  I checked dmesg when plugging it in after a reboot and created a mount point from there.

---

### Post by aquavitae on 2007-08-06
Great!

---

