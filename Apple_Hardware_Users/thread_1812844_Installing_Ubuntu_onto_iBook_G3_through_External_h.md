---
title: "Installing Ubuntu onto iBook G3 through External harddrive"
date: 2011-07-26
forum: Apple Hardware Users
---

### Post by ovlo99 on 2011-07-26
I have a iBook G3 that dosnt want to boot up at all. It makes the ding then a grey screen pops up. How do I install Ubuntu onto my iBook G3 with a external USB harddrive? is there a way?

---

### Post by Sef on 2011-07-27
Moved to Apple Forum.

---

### Post by 2F4U on 2011-07-27
I am just curious but isn't the G3 based on a PowerPC processor? Are you using the correct version of Ubuntu?

---

### Post by rsavage on 2011-07-27
Yes you should be able to install the latest ubuntu on an external hard drive. The problem is the ibook can't automatically boot from usb only firewire I think. So you will have to type in a short command through openfirmware to boot the usb hard drive, or setup a CD to boot the hard drive (assuming your internal hard drive is dead). It maybe worth running a live power pc ubuntu cd to check your internal hard drive. You only need a small (1MB) working partition to setup as a bootloader.
 
EDIT: it may be possible to setup the bootloader on your external hard drive.  It might just require a bit of manual adjustment.

---

### Post by linuxopjemac on 2011-07-27
[http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)

---

