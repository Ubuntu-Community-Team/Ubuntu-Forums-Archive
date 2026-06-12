---
title: "Unable to boot Ubuntu installation"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Jax Kovak on 2006-07-08
Well, Iv moved a little further on but things are now becoming too complex for me so I need some more help!

**RECAP**:
I have Windows 2000 installed (working) on hde1 (C:)
I have Windows XP installed (working) on hdf1 (G: on second HD)
I have Ubuntu installed (not booting) on hdf2 (Would be H: on second HD)

**The Cause of the problem**(as far as I can tell):
All booting is done by the Windows 2K Boot.ini - In other words the XP drive does not boot at all. I think that when Ubuntu was installed Grub was installed (or attempted to install) on the XP hard disk (hdf) but since this does not boot at all, this attempt failed.

I have now managed to mount hdf2 (Ubuntu) from the Live CD, and its all there. I reinstalled Grub to hdf2 (I wont install to the XP installation on hdf1) and it seems to have worked partially because using the GAG bootloader I can now get to the Grub boot menu for the first time! (Yay!!)

However, Grub cant load because in the menu.lst (I'm hoping I get all the names right because I'm in Windows right now) the boot device is set to "(hd2,1)" (which is of course hdf2), but when it tries to load from the Grub menu Grub says this partition does not exist.

On inspecting the /dev/ folder on my Ubuntu installation I cant see any 'hdxx' files at all, whereas in the Live CD there are quite a few.

**So the problem now**:
What is my drive meant to be called in the menu.lst on my Ubuntu installation?

Since I can mount the Ubuntu installation from the Live CD now I can manually edit this file.

Any help would be greatly appreciated.

Jax

---

### Post by catlett on 2006-07-08
You would have to post /grub/boot/menu.lst to be sure but if what you say is correct, the grub entry is wrong.
Grub counts 0 as 1 place meaning your second partition is 1 not 2.
If Ubuntu is on your second hard drives second partition (I am assuming that is it. hde is your first and hdf is the second. and hdf2 is the second partition)
You grub entry should be (hd1,1)

---

### Post by Jax Kovak on 2006-07-08
Hi, thanks catlett.

Iv just discovered Explore2fs, so I can now read the contents of the menu.lst, which is posted below (Iv taken what I assume are only the main relevant parts, rather than the whole thing, which seems to me mostly comments)

Also note that in the installation folder /dev/ there are no 'hdxx' files at all, just 'scdxx' or 'sgxx' (And I really don't know what else I'm looking at!)

```
title		Ubuntu, kernel 2.6.15-23-386
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdf2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdf2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by catlett on 2006-07-08
Right now grub is looking for Ubuntu on the 3rd hard drive's second partition. If you know Ubuntu is on the 2nd hard drive;s 2nd partition, then change every entry that is (hd2,1) to (hd1,1)

> title		Ubuntu, kernel 2.6.15-23-386
root		[COLOR="Red"](hd2,1)[/COLOR]
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdf2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		[COLOR="Red"](hd2,1)[/COLOR]
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdf2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		[COLOR="Red"](hd2,1)[/COLOR]
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1 Your list should look like this 
> title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdf2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdf2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Jax Kovak on 2006-07-08
Thanks for that! I'm off to the Live CD to edit that now. Ill let you know how I get on!

---

### Post by Jax Kovak on 2006-07-08
Thanks very much for that catlett you are a **[SIZE="5"]DIAMOND!![/SIZE]**

I'm now typing from within my Ubuntu installation for the first time since it was installed!

Excellent! =D>

All the best

Jax

---

### Post by catlett on 2006-07-08
GREAT. I love a good ending. See you around the forums.:D

---

