---
title: "Win2k problem"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by linuxfan64 on 2007-02-18
Hello, I just installed Ubuntu 6.06 on a dual-drive system. It installed and runs great, but when I go back to Windows 2000, it loads and runs extremely slowly and it locks up after it does manage to load. I don't have a RAID setup and the way I have the drives setup is that Linux is on the master drive and Win2k is on the slave.

Here is my boot list. I hope someone can figure this out. Thanks much,

Brian


title		Ubuntu, kernel 2.6.15-28-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb2
title		Microsoft Windows 2000 Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by jonathan.lees on 2007-02-18
Just a thought... how much disk space does the Windows 2000 partition have? As if there's no disk space you want have any room for the swap file and that'll slow things down.

---

### Post by linuxfan64 on 2007-02-18
Thanks for the tip. I went back and removed 3GB of programs and old files. Win2K is running better but still not like before.

---

