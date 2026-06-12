---
title: "dual boot issue"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by windowsatemyhomework on 2005-09-11
I installed ubuntu on the drive that is the master on my primary IDE. Windows XP is installed on SATA-4. If I set the SATA-4 drive to boot first, Windows starts with no OS selection menu. If Pri IDE is first in the boot order, I get an OS selection menu in which "Microsoft Windows XP Professional" doesn't work. When I select it, I get this message:
```
 Booting 'Microsoft Windows XP Professional'

root (hd1,0)
 Filesystem type unknown, partition type 0x7
savedefault
chainloader +1
```

Can anybody tell me how to fix this? Thanks.

---

### Post by poofyhairguy on 2005-09-11
Try this:

Boot up with your install disk and hit enter for the first 2 or 3 dialogs. The ones about keyboard and language settings. The install then will detect your hardware.
Wait a few seconds until it's done detecting the hardware and starts reading the package database.
Now hit ALT-F2 to go the the second vty. Hit enter here to login.
Now type this -> mkdir /ubu
Then this -> chroot /ubu
Then this -> grub-install /dev/hda

---

### Post by windowsatemyhomework on 2005-09-11
I tried that, pressing alt+F2 when it asked about partitions so as to be certain that all the relevant hardware was detected, but after "chroot /ubu" I got the message:
```
chroot: cannot execute /bin/sh: No such file or directory
```

---

