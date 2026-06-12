---
title: "Windows Partition and boot lost"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2007-11-12
I have a 300Gb harddrive, on which I have used GParted to repartition my harddrive to switch from a 100% use by windows to a 50-50 Linux and Windows.

Now I cannot mount the Windows drive in Linux and their is no grub menu.  As I have no experience with grub, can someone explain in depth what I need to do and how.

Also, I wonder should I use my windows recover CD or will this make it so I cannot boot Ubuntu?

---

### Post by madmatrixz3000 on 2007-11-12
I just was able to mount my drive, but what do I do to make XP bootable again?

---

### Post by LaRoza on 2007-11-12
Are you saying you cannot boot Windows, or you can not see the partition in Linux.

To repair the Windows boot loader, you can use the Super Grub Disk. This will make Ubuntu unbootable, but you can reinstall grub.

Post the contents of /boot/grub/menu.lst

---

### Post by Partyboi2 on 2007-11-12
You could try this one:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Hope it helps
:)

---

### Post by madmatrixz3000 on 2007-11-12
To clarify, I do not have a boot menu at startup.

I want a boot menu with these choices,

Ubuntu (Default)
Windows XP

Both are on the same SATA 300gb harddrive and now both are visible within my Ubuntu install

---

### Post by madmatrixz3000 on 2007-11-12
I have installed GRUB due the page you gave me.  If you don't see a positive repy, then I cannot boot ubuntu.

Here i go with the restart

---

### Post by LaRoza on 2007-11-12
Do you get a prompt saying to press ESC to see the menu? It may be there for a very short time.

You can edit /boot/grub/menu.list as root. "gksudo gedit /boot/grub/menu.lst" Comment out (put a # in front of) the "hiddenmenu" option.

Post the file here. If XP is not on the menu, it will be easy to add.

---

### Post by LaRoza on 2007-11-12
> **madmatrixz3000 said:**
> I have installed GRUB due the page you gave me.  If you don't see a positive repy, then I cannot boot ubuntu.

Here i go with the restart

If you cannot read this, use the Ubuntu live disk. 

Sorry, had to say that.

---

### Post by madmatrixz3000 on 2007-11-12
What?  I was able to edit the boot within my current install

---

### Post by madmatrixz3000 on 2007-11-12
Here is the list of Systems in Grub

> title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro single
initrd		/boot/initrd.img-2.6.22-12-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

How do I make a Windows one for XP on my other partition.  I don't know the #

---

### Post by LaRoza on 2007-11-12
```

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1

```

At this to it.
```

title Ubuntu 7.10, kernel 2.6.22-14-rt
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-rt root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-rt
quiet

title Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-rt root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro single
initrd /boot/initrd.img-2.6.22-14-rt

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, kernel 2.6.22-12-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-12-generic root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro quiet splash
initrd /boot/initrd.img-2.6.22-12-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-12-generic root=UUID=2d9d5102-92bd-4049-83f2-b7a288e5e4c0 ro single
initrd /boot/initrd.img-2.6.22-12-generic

title Ubuntu 7.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1


```

---

