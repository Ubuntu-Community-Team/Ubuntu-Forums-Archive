---
title: "kubuntu 7.10 usb detection problem"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2007-12-15
i have installed kubutnu 7.10 few minutes ago but it can't detect my usb. tell me how to access it. in previous kubuntu version of dapper this problem was there. is there any solutin of this problem?

---

### Post by kajillin on 2007-12-15
Is it just a device thats not being detected, or a usb port (or all of them)

---

### Post by u04f061 on 2007-12-15
so far i have kingston usb data traveler, which is not being detected.

---

### Post by kajillin on 2007-12-15
well as far as i know automounting usb drive in 7.10 doesnt work to well, so have you tried a manual mount through the terminal? Also do an update then restart and see if it will auto mount u might just have an out dated package somewhere. Also make sure your motherboard has turned on the usb ports a simple mistake but common. And dont plug the drive in before the restart do it after, that might help.

if all else fails us google.

Cheers,

---

### Post by u04f061 on 2007-12-15
how to mount usb manually through terminal?

---

### Post by pisewip on 2008-01-12
you have to create a directory, usually in /mnt or in /media.

ex. sudo mkdir /mnt/mydevice

then you have to locate which usb you have to mount, you can find it running dmesg after you plugged the usb.
 
You would see at last line of dmesg the device detection and the name assigned.
ex. it would be sdb1 or sda1 

then you have to mount the device

sudo mount /dev/sdb1 /mnt/mydevice

then you can surf your device cd /mnt/mydevice.

---

