---
title: "editting menu.lst on other partition"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-04-19
I want to be able to edit the menu.lst file on another linux distro. It is on another partition and when I open it with KWrite  it wont let me save changes - access denied cannot write to ....


any thoughts on how to do this?

---

### Post by igknighted on 2007-04-19
> **tchoklat said:**
> I want to be able to edit the menu.lst file on another linux distro. It is on another partition and when I open it with KWrite  it wont let me save changes - access denied cannot write to ....


any thoughts on how to do this?

Try opening it as root "sudo kwrite /mount/point/boot/grub/menu.lst", where /mount/point/ is where you mounted the drive

---

### Post by tchoklat on 2007-04-19
tried that but I cannot work out the path to the file to use the sudo command;

Disk /dev/sda: 320.0 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2459    19751886    7  HPFS/NTFS
/dev/sda2            2460        2472      104422+  83  Linux
/dev/sda3   *        2473       10000    60468660   83  Linux
/dev/sda4           10001       38913   232243672+   5  Extended
/dev/sda5           10001       20000    80324968+  83  Linux
/dev/sda6           20001       34260   114543418+  83  Linux
/dev/sda7           34261       38637    35158221   83  Linux
/dev/sda8           38638       38913     2216938+  82  Linux swap / Solaris


The OS whose menu.lst I need to edit is on sda7. I boot from sda3


tchoklat

---

### Post by Pobega on 2007-04-19
```
mount /dev/sda7 /mnt
gksudo kwrite /mnt/boot/grub/menu.lst
umount /dev/sda7
```

Should work perfectly fine. You may also want to put sda7 in your /etc/fstab, but that's up to you.

---

### Post by tchoklat on 2007-04-19
that's helpful, thanks!

---

