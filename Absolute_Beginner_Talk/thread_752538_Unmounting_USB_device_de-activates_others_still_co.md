---
title: "Unmounting USB device de-activates others still connected"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Lourie2 on 2008-04-11
Whenever I unmount a USB device, eg. external HD or CD-writer or iPod, my USB wireless adapter stops functioning.  Then I have to reboot.  Any advice, please?

---

### Post by Biggy on 2008-04-11
right click in device you want to disconect and click 'Unmount Volume'

---

### Post by Lourie2 on 2008-04-11
That is the way I unmount USB devices, that's not the problem, the problem is the USB device still supposed to be connected (my USB wireless adapter) stops functioning

---

### Post by TeoBigusGeekus on 2008-04-11
Have you tried to unmount the device through terminal?
```
sudo umount /media/nameofdisk
```

---

### Post by Lourie2 on 2008-04-12
Unmounting through the Terminal still does not help.  It unmounts the disk, but when I remove it from the USB slot, I lose connectivity of my wireless adapter.

---

