---
title: "Setting up XP in grub"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Milner_07 on 2007-03-06
Ok then i have read all of the documentation on this but i want to make shore i get it perfectly right for my needs.

I currently have windows installed on a sata hard drive and ubuntu (and all my windows files) of a IDE hard drive. Both have there pins set to master. Currently the SATA Drive is the one the is booted from automatically but i can change that if this works.

Hears my fdisk if that helps:
```
sudo fdisk -l

Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       27328   219512128+   7  HPFS/NTFS** - All my windows files**
/dev/hda2           27329       30515    25599577+   5  Extended
/dev/hda5           27329       27583     2048256   82  Linux swap / Solaris
/dev/hda6           27584       28858    10241406   83  Linux** - Ubuntu**
/dev/hda7           28859       30515    13309821   83  Linux** - /Home**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS** - Windows**
```

And hears the bit of my grub menu.lst i think i need to edit 

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

So can any one tell my how i go about adding a section for windows XP that will make it think its the master?

Thanks 

TM

---

### Post by dstew on 2007-03-06
I am not sure about how your BIOS numbers drives, but if you want to boot windows from any hard drive other than the first, you have to "map" the second drive onto the first drive name in grub. That is, if dev/hda is numbered as hd0 by your BIOS, and dev/sda is hd1, then before you boot, you have to tell grub to map hd1 onto hd0. See [http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

My guess is that you will have to add the following to your menu.lst file:

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
chainloader +1
makeactive
boot

I am not completely sure, you might want to hunt for some examples.

---

