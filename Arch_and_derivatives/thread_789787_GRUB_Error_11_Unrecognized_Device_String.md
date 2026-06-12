---
title: "GRUB Error 11: Unrecognized Device String"
date: 2008-05-10
forum: Arch and derivatives
---

### Post by b0uncyfr0 on 2008-05-10
This just popped out of nowhere. i tried reinstalling GRUB with a livecd but that didn't work. This is on a fresh install from last night. This morning just rebooted and BAM. The Windows option still works though..

Heres my menu.lst

# (0) Arch Linux
title  Arch Linux
root  (hd0,2)
kernel /boot/vmlinuz26
root=/dev/disk/by-uuid/a9341d88-bf3b-4dfe-a46d-46c38b2c2224 ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root  (hd0,2)
kernel /boot/vmlinuz26
root=/dev/disk/by-uuid/a9341d88-bf3b-4dfe-a46d-46c38b2c2224 ro
initrd /boot/kernel26-fallback.img

How can i check the uuid strings?

---

### Post by finferflu on 2008-05-11
I guess this is a starting point: [http://wiki.archlinux.org/index.php/Persistent_block_device_naming](http://wiki.archlinux.org/index.php/Persistent_block_device_naming)

---

### Post by b0uncyfr0 on 2008-05-13
I finally fixed it. kernel /boot/vmlinuz26 and root=/dev/disk/by-uuid/a9341d88-bf3b-4dfe-a46d-46c38b2c2224 ro are supposed to be on the same line.

Thanks for the info finferflu.

---

