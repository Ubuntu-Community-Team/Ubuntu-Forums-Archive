---
title: "installing xubuntu from hard drive"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by rienfleche on 2006-06-12
does anybody know how i can install xubuntu onto my win98 system without a cdrom or floppy drive.  i cannot boot from usb.

system specs if you need them
acer travelmate 343T
500MHz Pentium III
128MbRAM
approx 10 gb hard drive

---

### Post by Kalvin on 2006-06-12
Haven't tried it, but here's a Wiki entry on this very issue.

[https://wiki.ubuntu.com/Installation/FromWindows?highlight=%28install%29]("https://wiki.ubuntu.com/Installation/FromWindows?highlight=%28install%29")

---

### Post by aysiu on 2006-06-12
[This](http://www.ubuntuforums.org/showthread.php?t=28948) may help.

---

### Post by rienfleche on 2006-06-20
i get this error when booting loadlin:

invalid compressed format (err=1)
VFS: Cannot open root device "rd/0" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernal Panic - not synching: VFS: Unable to mount root fs on unknown-block(0,0)

i got the initrd and linux file from here:
[http://mirror.optus.net/ubuntu/dists/dapper/main/daily-installer-i386/current/images/netboot/ubuntu-installer/i386/](http://mirror.optus.net/ubuntu/dists/dapper/main/daily-installer-i386/current/images/netboot/ubuntu-installer/i386/)

help is appreciated, if possible.

---

### Post by Kuraboy on 2006-06-20
hi!

I too downloaded the linux and initrdg.gz and typed

**loadlin linux initrd=initrd.gz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --**

and I got the same problem:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I tried vmlinuz instead of linux and typed:

[B]loadlin vmlinuz initrd=initrd.gz root=/dev/ram0
[/B]
but still smae problem, any help apriciated!!! and need please!

---

