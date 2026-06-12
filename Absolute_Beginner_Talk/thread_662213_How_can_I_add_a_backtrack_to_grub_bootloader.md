---
title: "How can I add a backtrack to grub bootloader"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by kditty on 2008-01-08
i installed backtrack v3 to an internal second HD (HDD) VIA: [http://backtrack.offensive-security.com/index.php/Howto:Install_GUI](http://backtrack.offensive-security.com/index.php/Howto:Install_GUI)

i can not get backtrack to boot from grub menu. i followed all instructions there, but replaced hda1 with hdd1any help on this is much appreciated. thanks in advance

my current grub menu.list:

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bc07d297-9e01-457c-922e-eee76db881fa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bc07d297-9e01-457c-922e-eee76db881fa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bc07d297-9e01-457c-922e-eee76db881fa ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bc07d297-9e01-457c-922e-eee76db881fa ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bc07d297-9e01-457c-922e-eee76db881fa ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bc07d297-9e01-457c-922e-eee76db881fa ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title BackTrack

root (hd1,3)

kernel /boot/vmlinuz ro root=/dev/hdd4

boot
```

---

### Post by aselya1 on 2008-01-14
Are you positive that (hd1,3) is the correct location of your Backtrack partition? Under this scheme, it would be the fourth partition on the second drive. Since the drive is hdd, I might suggest that its actually a later drive in the boot sequence. One easy way that you can test this out is to edit the GRUB lines at boot. When you attempt to boot from the Backtrack title but it doesn't work (Partition not found, press any key or whatever), return to the GRUB menu, highlight the title and press e to edit it. It will then show you the separate lines that it has loaded for the title. You can then highlight the root (hd1,3) line, press e again to edit this line, change it to something else like (hd2,3), press enter and then b to attempt to boot using the new root value. If this doesn't work again, you can go back and try something else. Eventually what you find to be the correct drive number should be permanently written to the GRUB menu by editing menu.lst (but I'm sure you know how to do this as you've already gotten the Backtrack title in there).
Another thing to check is that the partition that Backtrack is on is set as bootable. You can use Gparted or fdisk to check this.
Keep posting here if you have more problems, or if its fixed.

---

