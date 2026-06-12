---
title: "change default mount command"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by litmos95 on 2007-08-25
hi everyones
every time i plug the usb cabel of my ntfs ext hdd, i get an error message because it is scheduled to be checked by windows. I can use the command 
```
mount -t ntfs-3g /dev/sdb1 /media/ext -o force
```
to force it and it works. But how can I change the default mount command so that instead of this error message it can be mounted directly?

thanks in advance

---

### Post by mlentink on 2007-08-25
Would it be possible to post the error message?  As of now, I have trouble understanding your problem. I don't really see what 'scheduled to be checked by windows' has to do with it.

---

### Post by litmos95 on 2007-08-25
the error message:
Volume is scheduled for check. Please boot into Windows TWICE, or use the 'force' mount option. For example type on the command line: mount -t ntfs-3g /dev/sdb1 /media/Samsung -o force Or add the option to the relevant row in the /etc/fstab file: dev/sdb1 /media/Samsung ntfs-3g defaults, force 0 0

---

### Post by mlentink on 2007-08-25
Ok, I've never seen that before, but hey, I'm a relative beginner in Ubuntu too.
How about trying to do exactly what it says?
First try booting into windows twice, see if that fixes it. You may have to use the Windows utilities to check that disk. If that doesn't work, open up /etc/fstab with your favorite text-editor and change it like the error message says. 
See if that works.

---

### Post by alienexplorers on 2007-08-25
May be a dumb question, but in the media directory are you sure Samsung is written with a capital "S" and not a small "s".  You could also boot windows and run check disk on the drive and see if any errors come up.

---

### Post by litmos95 on 2007-08-25
> **mlentink said:**
> Ok, I've never seen that before, but hey, I'm a relative beginner in Ubuntu too.
How about trying to do exactly what it says?
First try booting into windows twice, see if that fixes it. You may have to use the Windows utilities to check that disk. If that doesn't work, open up /etc/fstab with your favorite text-editor and change it like the error message says. 
See if that works.

Of course i've done all that. if I edit the fstab, it can only be mounted if the cable is plugged from the system start, since that is actually a solution for internal hdd. Otherwise the external hdd won't be mounted. And yes, i have also let windows check it and also boot windows twice with the hdd plugged. It didn't work.

---

