---
title: "Okay, newb question"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by faultedperfection on 2007-01-22
Okay so I dual boot with windows xp, and after installing Ubuntu I updated it, and now I have for entries for ubuntu, and the one for xp, I was wondering how you got rid of the two extra entries that I no longer use. I guess what I am asking is how do I edit the Grub Menu?

Thanks

---

### Post by Sqwishy on 2007-01-22
open console/terminal and type
```
sudo gedit /boot/grub/menu.lst 
``` that's how you edit it it should work. i dono maybe it's /boot/grub/grub.conf

---

### Post by Malac on 2007-01-22
As sqwishy said sudo gedit /boot/grub/menu.lst
but if you delete the entries they will just get put back in the next time you do a kernel update.
You should put a # before the line of the section you don't want to see.
e.g.```
title        Ubuntu, kernel memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin 
boot
```becomes:```
#title        Ubuntu, kernel memtest86+
#root        (hd0,1)
#kernel        /boot/memtest86+.bin 
#boot
```[B][U]OR
[/U][/B]If you want to get rid of the kernel of the old version off your disk to free up space.
Synaptic Package Manager and search for "linux-image"  and mark the old one for removal.

---

