---
title: "install ubuntu from hard disk"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by morphixrocks on 2006-01-28
hi 

any way to install ubuntu from iso image, which is in vector linux. i dont have cd rom drive

---

### Post by kaamos on 2006-01-28
I guess it could be done.. Try searching in the ubuntu wiki. Here is one link [https://wiki.ubuntu.com/Installation/FromAnotherDistro](https://wiki.ubuntu.com/Installation/FromAnotherDistro)

---

### Post by lha on 2006-01-28
I have used netinstall to install Ubuntu without a cd. You need an internet connection to do this, but it's much easier than that FromAnotherDistro. (I have done this with loadlin and Win98 but I can't see a reason why it wouldn't work with any Linux distro and grub or other boot loader.)

Copy files initrd.gz and linux to your /boot. Grab them from install/netboot/ubuntu-installer/i386 on install cd or [online]("http://http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/"). Add following lines to menu.lst:
```
title Install Ubuntu
root (hd0,0)
kernel /boot/linux vga=normal ramdisk_size=16384 root=/dev/rd/0 rw --
initrd /boot/initrd.gz
```
Change (hd0,0) to correct device. Restart and start installer.

PS. I'm not sure what will happen if you erase the partition where you have linux and initrd.gz. Maybe it won't hurt, maybe it will.

---

