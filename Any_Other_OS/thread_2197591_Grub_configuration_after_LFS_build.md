---
title: "Grub configuration after LFS build"
date: 2014-01-04
forum: Any Other OS
---

### Post by Tristan_Williams on 2014-01-04
I am running Ubuntu minimal 13.10.
I have just finished with Linux from Scratch.
I installed LFS on a dedicated HDD and installed Grub.
However, when I go to boot, it says "File not found"

I don't understand Grub in any way, so I have no idea how to fix this.



While in Ubuntu:
LFS partition = /dev/sdb1
LFS kernel = linux-3.10.10


Here is my /boot/grub/grub.cfg file:
```

# Begin /boot/grub/grub.cfg
set default=0
set timeout=5

insmod ext2
set root=(hd0,2)

menuentry "GNU/Linux, Linux 3.10.10-lfs-7.4" {
        linux   /boot/vmlinuz-3.10.10-lfs-7.4 root=/dev/sda2 ro
}

```

I really can't figure out what's wrong here... please help.

---

### Post by Bucky Ball on 2014-01-04
*Thread moved to **Other OS/Distro Support**.*

---

