---
title: "Removing Mounted Icon From Desktop?"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by Phixion on 2006-03-07
Hi, how can I remove my mounted partition Icon from my desktop? And what should be in my /etc/fstab exactly? I think its this that controls whether the Icon is shown or not if I remember correctly.

Also I just install VLC player and noticed that the sound isn't working for it... the sounds working in everything else though.

And one more thing (sorry) my alsamixer settings keep resetting to 0 volume when I reboot, Is there anyway to stop that happening?

Thanks :D

---

### Post by matthewv on 2006-03-07
There is a property in gconf that can change the displaying of volumes on the desktop.. I doubt fstab would change it at all...

Press Alt-F2 and run the command ```
gconf-editor
```
Then go to /Apps/Nautilus/Desktop and deselect volumes_visible

---

### Post by Phixion on 2006-03-07
Thanks alot! It's been a while since I had to do this :)

Any ideas on my other questions?

---

### Post by craig552 on 2006-03-08
Is it possible to show desktop icons for some volumes, but not for others? 
I would like the Icon for removeable devices (usb stick, dvd etc..) but not for permanently connected devices (Windows HDD).
Is this possible?

---

### Post by kaamos on 2006-03-08
If you mount the win hdd under /mnt, it will not show up on the desktop. If you have volumes_visible checked in gconf, usb sticks and dvds will show up because they are mounted under /media.

For vlc, go to preferences -> audio -> output modules, check the advanced options box and try different outputs (alsa, oss..).

---

