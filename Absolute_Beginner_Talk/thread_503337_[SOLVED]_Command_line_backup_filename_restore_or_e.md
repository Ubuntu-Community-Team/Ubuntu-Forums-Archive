---
title: "[SOLVED] Command line backup filename restore or edit via vi"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-07-17
Working in Grub, i made a backup copy. Edited the grubfile menu.lst

Rebooted and X server failed . . .

dumb as this seems, please spell out the syntax to do the restore from the command line.

I think it's:

mv /boot/grub/menu.lst-backup menu.lst

but if I'm wrong, I would like to not make the other problems I'm having an even greater burden to fix. (Yes, I did do man mv)

If this was say the repositories list, I could break it and not worry too much, but menu.lst is too big a deal to $T$Y^Y$Y up!

---

### Post by raja on 2007-07-17
That is right. That will rename the backup file as the new menu.lst.

You can also edit grub during boot up itself (meaning you dont have to boot up into the system from another os or a live cd to edit it. You can press 'e' to go to edit mode when the boot options are shown and then edit the line that you think is the offender. If it works and you boot fine, you can edit it to make the changes permanent.

---

### Post by UltraMathMan on 2007-07-17
Unless you are in /boot/grub you would need to specify the destination path as well as the location path, ie ```
mv /boot/grub/menu.lst-backup /boot/grub/menu.lst
```

-Hope this helps :)

---

### Post by Mark_in_Hollywood on 2007-07-17
Oddly enough:

using the live cd:

sudo su and become superuser root

cd /media/disk/boot/grub

ls

sudo gedit /media/disk/boot/grub/menu.lst

and lo! and behold! it worked.

---

