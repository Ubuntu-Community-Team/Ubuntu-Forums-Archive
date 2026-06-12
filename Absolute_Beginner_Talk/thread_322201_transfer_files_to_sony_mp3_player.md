---
title: "transfer files to sony mp3 player"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-12-20
i have an sony mp3 player (Network Walkman NW-E53) and i want to copy some mp3 on it. how do i proceed?
this is the output of "dmesg"
> 
[17179723.156000] usbcore: registered new driver usb-storage
[17179723.156000] USB Mass Storage support registered.
[17179723.156000] usb-storage: device found at 2
[17179723.156000] usb-storage: waiting for device to settle before scanning
[17179728.156000] usb-storage: device scan complete
[17179728.160000]   Vendor: SONY      Model: NETWORK  WALKMAN  Rev: 1.00
[17179728.160000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179728.248000] SCSI device sda: 249344 512-byte hdwr sectors (128 MB)
[17179728.252000] sda: Write Protect is off



---

### Post by kd_pease on 2006-12-20
Does a disk icon appear on your desktop when you plug the mp3 player in? If it does, you should just be able to copy files to that disk. If not you might need to mount it. To mount the disk, create a directory somewhere and type: 

sudo mount /dev/sda /path/to/your/directory

into a terminal window. If you don't get any errors you should be able to browse to the directory through nautilus and copy files in that way. Don't forget to do a:

sudo umount /dev/sda

before you unplug the mp3 player.

---

### Post by dcstar on 2007-03-18
> **mendingo84 said:**
> i have an sony mp3 player (Network Walkman NW-E53) and i want to copy some mp3 on it. how do i proceed?
this is the output of "dmesg"

This might help:

[http://david.dw-perspective.org.uk/Sony-NW-E00X-Walkman-On-Linux-FreeBSD-MacOSX-etc.html](http://david.dw-perspective.org.uk/Sony-NW-E00X-Walkman-On-Linux-FreeBSD-MacOSX-etc.html)

I have just got a NW-E405 and the Linux software runs, but all the files on the player don't work and I get error messages.

I have gone back to booting Windows and using the Sony supplied software when I need to upload tracks to the player.

---

### Post by antonr on 2008-03-06
There is a java program called JSymphonic which may help. I just got it working yesterday with a Sony Walkman MP3 player NW-E003F.
Search for my HOWTO in these forums.

---

### Post by tgalati4 on 2008-03-06
[http://sourceforge.net/project/showfiles.php?group_id=190494](http://sourceforge.net/project/showfiles.php?group_id=190494)

---

