---
title: "Help! Please"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by mbv93 on 2006-12-17
hey i have ubuntu edgy eft on my computer that-s all i have but i had grub i wanted to uninstall it so i tried to uninstall typing fixmbr on the recovery console of the windows xp cd and now when i turn on my computer i get a message that says error loading operating system it-s still there but i cant load it help me!

---

### Post by macogw on 2006-12-17
If you don't have Windows, you can't use the Windows bootloader.  You have to use a Linux one--either Lilo or Grub.  Reinstall Grub from the Livecd.

---

### Post by mbv93 on 2006-12-17
could you help a little i-m on the live cd but where or how do i reinstall grub :)

---

### Post by macogw on 2006-12-17
trying to remember...
```

sudo -s
mount /dev/hda (if that's your hard drive, sda if that's what it's called) /mnt
chroot /mnt
apt-get install grub

```
I think that should do it.

---

### Post by mbv93 on 2006-12-18
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# mount /dev/hda  /mnt
mount: you must specify the filesystem type
root@ubuntu:~# chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
root@ubuntu:~# apt-get install grub
this is what ia get putting the code :mad:

---

