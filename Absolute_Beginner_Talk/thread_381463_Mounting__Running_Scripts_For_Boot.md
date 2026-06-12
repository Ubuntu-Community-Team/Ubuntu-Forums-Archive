---
title: "Mounting / Running Scripts For Boot"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by soul814 on 2007-03-10
How would I mount a hard drive and a SD card on boot. This is on a notebook. Also if there were other scripts / commands I wanted to run on boot how would I do this? 

Another question, how would I remove say the hda1 drive from my desktop without unmounting the drive itself. Thanks

---

### Post by K.Mandla on 2007-03-10
> **soul814 said:**
> How would I mount a hard drive and a SD card on boot. This is on a notebook. 
If you know the drive assignment for the SD card, you should be able to add it to your fstab. Just as an example, if your card is /dev/sda1, the mountpoint is /media/sdcard and the filesystem is FAT16, I believe this might do the trick:

```
/dev/sda1 /media/sdcard vfat defaults,auto 0 0
```
I might be slightly off on that one, because I'm making it up from memory while I'm at work.

> **soul814 said:**
> Also if there were other scripts / commands I wanted to run on boot how would I do this? 
I think rc.local is somewhere in the /etc folder, and might be what you're looking for. 

> **soul814 said:**
> Another question, how would I remove say the hda1 drive from my desktop without unmounting the drive itself. Thanks
Do you mean you don't want the icon on your desktop? Or you want to actually remove the drive but keep the device assignment?

---

### Post by soul814 on 2007-03-11
Thanks for the reply, I'm going to reboot now and see if that did the trick. But I meant just remove the icon from the desktop without unmounting the drive.

---

