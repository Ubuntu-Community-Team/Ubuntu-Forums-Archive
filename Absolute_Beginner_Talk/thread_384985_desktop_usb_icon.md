---
title: "desktop usb icon"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by heatrag on 2007-03-15
I'm trying to get my USB memory card to mount on the Desktop can some one tell me where I'm going wrong?

sudo mount /dev/<mount point> <path to where you want files mounted>

richard@heatrag:~$ sudo mount /media/usbdisk Desktop
mount: /media/usbdisk is not a block device
richard@heatrag:~$ sudo mount dev/media/usbdisk Desktop
mount: special device dev/media/usbdisk does not exist
richard@heatrag:~$

---

### Post by 23meg on 2007-03-15
Can you view the contents of your memory card? Is it shown in Places / Computer?

---

### Post by heatrag on 2007-03-15
where is Places / Computer, I'm on xubuntu.
thanks,
 it used to mount once

---

### Post by reclusivemonkey on 2007-03-15
As 23meg said, it should automatically mount. However if it isn't doing and you want to mount it manually, then I would to the following;
[LIST=1]
[*]Unplug your USB memory stick
[*]tail -f /var/log/messages
[*]Plug in your memory stick and look for a message about a /dev being recognised (like /dev/sda1)
[*]sudo mkdir /media/*<directory>*
[*]sudo mount /dev/*<your device>* /media/*<directory>*
[/LIST]

Where *directory* is what you want the directory to be called. I think you were getting confused between where the device is mounted, and what the device is called in your previous posts. Also, the correct path for desktop (in Gnome at least) is either

/home/*username*/Desktop

or

~/Desktop

---

