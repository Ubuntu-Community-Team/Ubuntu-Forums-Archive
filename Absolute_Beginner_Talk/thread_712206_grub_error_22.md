---
title: "grub error 22"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by moparmudder420 on 2008-03-01
hi, ive messed around with ubuntu b4, a friend of mine deleted my ubuntu partition, now i get grub error 22, which means it cant find ubuntu partition, is there n e way from the terminal i can uninstall grub, i have vista, so would i be able to use an xp recovery disk from another pc to get into dos command line, i only need to boot into vista once so i can resize the drive and make a partition again, gparted takes way too long, and i also dont have a vista reccovery cd

thanks

---

### Post by taurus on 2008-03-01
Or you can use this to remove GRUB from MBR, [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

---

### Post by moparmudder420 on 2008-03-01
im running off of the live cd right now, but i will dl onto usb stikk, ill let u kno
thanks

---

### Post by bumanie on 2008-03-01
Unfortunately, although xp will recognize vista's partition, it will not be able to change anything in vista. As far as I understand, the bootloader is different, so xp can't repair vista's mbr. Your best bet would be to remove grub as suggeted above.

---

### Post by moparmudder420 on 2008-03-01
also, if i use super grub, and delete grub, will vistas bootloader show up?

---

### Post by bumanie on 2008-03-01
I have never tried this myself, therefore cannot say for sure, there is a risk that you may end up with a corrupted vista mbr (not 100% sure on that). Read herman's (tarus' link) site. There is heaps of information and work arounds on there re grub. 
If Herman's site doesn't sort out your problem and as you don't have vista recovery etc. you may have to try something a little more radical like downloading test disk and getting it to either recover your original vista installation or use it to fix the corrupt mbr (if that's what it ends up). As I said, a bit radical, but apparently works well on data recovery and also can resurrect corrupt mbr's.
Sorry I can't be more specific.

---

### Post by moparmudder420 on 2008-03-01
i am also wondering if i delete the partition on my old ipod that i do not use ne more, can i install ubuntu on that, its 4.1 gb

---

