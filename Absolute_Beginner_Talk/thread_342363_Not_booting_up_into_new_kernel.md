---
title: "Not booting up into new kernel"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by x4nth3r on 2007-01-19
I've installed a new kernel but i can't boot into it as it doesn't show up in grub. How do i fix this?

---

### Post by bodhi.zazen on 2007-01-19
What kernel ?

If you do not know: ```
ls /boot
```

We need the exact name vmlinux-xyz

Now we can edit /boot/grub/menu.lst:```
gksudo gedit /boot/grub/menu.lst
```

We need to add something like this:

title Ubuntu kernel xyz
root (hdx,y)
kernel /boot/vmlinuz_the_one_you_want_to_boot root=/dev/hdxy ro splash quite
initrd /boot/initrd_the_one_you_want_same_numbers_as_kernel.img
savedefault
boot

---

### Post by x4nth3r on 2007-01-20
abi-2.6.17-10-generic         memtest86+.bin
config-2.6.17-10-generic      System.map-2.6.17-10-generic
grub                          vmlinuz-2.6.17-10-generic
initrd.img-2.6.17-10-generic

This is what shows up on the ls /boot

---

### Post by bodhi.zazen on 2007-01-20
The entry you want;

```
gksudo gedit /boot/grub/menu.lst
```

> title           Ubuntu, kernel 2.6.17-10-generic
root (hdx,y)
savedefault
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdxy ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic

You need to change (hdx,y) and /dev/hdxy to the actual numbers on your Ubuntu partition.

If you do not know them, get root (hdx,y) and root=/dev/hdxy from your current entry.

If kernel 2.6.17-10-generic is not you new kernel, it then looks like you need to re-install the kernel you want :p

---

### Post by po0f on 2007-01-20
x4nth3r,

How did you install this new kernel?  Are you talking about a kernel from the repos or a kernel you custom-compiled?  All I see in your /boot directory is a stock Ubuntu kernel.

---

### Post by x4nth3r on 2007-01-20
The new kernel is custom complied. I just followed a guide somewhere but i can't find it anymore.

---

### Post by po0f on 2007-01-20
x4nth3r,

From the directory of the kernel's source:
```
[FONT="Courier New"]$ find . -type f -iname "bzImage"[/FONT]
```
This is the actual kernel.  When you find it copy it, as well as .config and System.map, to /boot:
```
[FONT="Courier New"]$ sudo cp path/to/bzImage /boot/kernel-<kernel_version>
$ sudo cp .config /boot/config-<kernel_version>
$ sudo cp System.map /boot/System.map-<kernel_version>[/FONT]
```
Be sure to replace <kernel_version> with whatever version the kernel is you compiled.  ;)

[EDIT]

IIRC, bzImage will be in boot/<arch>/bzImage.

---

