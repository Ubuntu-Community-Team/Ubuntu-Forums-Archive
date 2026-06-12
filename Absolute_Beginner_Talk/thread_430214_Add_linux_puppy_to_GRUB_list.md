---
title: "Add linux puppy to GRUB list"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-01
How can i add Linux puppy to my GRUB menu.lst? My puppy partion is on /dev/sda6

---

### Post by 5-HT on 2007-05-02
You'll need to edit /boot/grub/menu.lst to add the entry after ```
### END DEBIAN AUTOMAGIC KERNELS LIST
``````

title        Puppy Linux (edit to your liking)
root        (hd0,5)
kernel        (add the kernel path, it should be in /boot somewhere) root=/dev/sda6 ro single
initrd        (add the path to puppy's initrd)
quiet
savedefault

```Take a look at Ubuntu's entries in menu.lst to get an idea, the file is nicely commented.

Your 'root' line will be (hd0,5)


e.g., something along these lines (my grub entry)

```
title        Ubuntu, kernel 2.6.21-custom
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.21-custom root=/dev/sda3 ro 
initrd        /boot/initrd.img-2.6.21-custom
quiet
savedefault 
```

---

### Post by mojo123 on 2007-05-02
Mine doesnt work this is what i have

title		Puppy Linux 
root		(hd0,5) 
kernel		/boot/vmlinuz 
root=/dev/ram0 
initrd		/boot/initrd.gz

It sais invalid string or something like that!

---

### Post by mojo123 on 2007-05-03
anyone know?

---

### Post by pdrift on 2007-05-06
hey guys i'm having the same problem. at first i installed pupy linux on my 2gb cruzer micro
and it worked fine. if i plugged it in the usb before booting up, it booted up puppy automatically.
if it wasn't [lugged in, feisty would boot up. but now for some reason it will not boot off my usb drive any more. it says missing operating system. 
so i've been trying to edit my menu.lst file so that i could choose puppy or feisty from the list
but i can't get it to work.

here's my output from fdisk:

     pdrift@mybu:~$ sudo fdisk -lu
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   153340424    76670181   83  Linux
/dev/sda2       153340425   156296384     1477980    5  Extended
/dev/sda5       153340488   156296384     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 2055 MB, 2055021056 bytes
64 heads, 62 sectors/track, 1011 cylinders, total 4013713 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     4011647     2005793    6  FAT16
pdrift@mybu:~$ 



i'm guessing that it is /dev/sdb, right
so what would that be in the menu.lst

heres the end of my menu.lst

     title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8d531ef2-d598-4357-895e-2c73796d0d3b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8d531ef2-d598-4357-895e-2c73796d0d3b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Puppy
root		(sda,0)
kernel		/vmlinuz root=/dev/sdb ro
initrd		/zdrv_215.sfs
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


can anyone help with this?
does anyone know why it stopped booting up from my  usb drive to begin with?

i tried reinstalling puppy several times i even reformatted the drive but
i can't get it.

---

### Post by annda on 2007-05-06
check the paths for your boot images.

i don't know how good puppy is with support, but you need different boot options with each distro. try to search wikis and google. as an example of differences (not to be followed) is my clean entry for gentoo (hd0,6 is sda7):

title		gentoo-2.6.20
root		(hd0,6)
kernel		/boot/kernel-genkernel-x86-2.6.20-gentoo-r6 ro root=/dev/ram0 init=/linuxrc real_root=/dev/sda7
initrd		/boot/initramfs-genkernel-x86-2.6.20-gentoo-r6

@pdrift: root (sda,0) does not look good. you need something like (hd1,0)...

---

