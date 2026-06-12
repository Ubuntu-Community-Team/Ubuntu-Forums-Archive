---
title: "startup splash screen (removal)"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-12-05
Is there anyway to get back to the original LiNuX bootup commandline prompt?
I actually like watching that scroll by since it told alot more then what the UBUNTU (with progress bar) splash screen gives.

---

### Post by aysiu on 2005-12-05
```
sudo nano /boot/grub/menu.lst
``` Take the word *splash* off the kernel put of the boot entry. Afterwards, it should look something like this: ```
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet
``` instead of ```
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet splash
```

---

### Post by nitricacid on 2005-12-06
Thanks :)

---

