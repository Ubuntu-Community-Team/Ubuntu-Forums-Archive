---
title: "EXT HDD unmounts(?) after some period of time..."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by morequende on 2007-06-16
Hi! I've recently bought an external usb hdd. I've installed ntfs-3g and it's working fine. I can read and write to the external disk. But, after some period of time, when I try to open the external disk i get this message.

Could not show 'file:///media/Abyss'
I/O error

If I unplug the disk and then plug it in again it works fine, but after a while I get the same error when I try to open it.

Any ideas?

---

### Post by Golyadkin on 2007-06-16
This is a known bug with the IDLE state of the USB device. I will look if I can find something about it, I saw this problem several times already on these forums.

---

### Post by Golyadkin on 2007-06-16
I think it has to do with this bug: 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/43875](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/43875)

It is something with suspend mode in USB devices.

---

### Post by morequende on 2007-06-16
Ok, thanks, I'll give it a try when it stops working... Thanks :D

---

