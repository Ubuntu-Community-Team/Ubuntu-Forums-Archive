---
title: "Double Ubuntu Entries in GRUB?"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-02-13
Recently when I allowed Ubunto 6.10 to update, my GRUB menu was effected.  I now have double entries for Ubuntu.
Here's what I now have listed in GRUB:

> title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other Operating Systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Here are my my questions --
(1)  Can I safely delete the kernel 2.6.17.10 entires or should I just leave this alone in GRUB?  (2) If this appears in GRUB, does this kernel appear elsewhere in the system and should any the kernel 2.6.17.10 be removed?

---

### Post by Crooksey on 2007-02-13
Its because a new kernel has been installed, if you are booting into the top kernel with no issues its fine to delete the lines, or better yet just comment them out, so if your 2.6.17-11 kernel craps out you can boot into 2.6.17-10

Copy and paste the following in:

```

title Ubuntu, kernel 2.6.17-11-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro single
initrd /boot/initrd.img-2.6.17-11-generic
boot

#title Ubuntu, kernel 2.6.17-10-generic
#root (hd1,0)
#kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash
#initrd /boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root (hd1,0)
#kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single
#initrd /boot/initrd.img-2.6.17-10-generic
#boot

title Ubuntu, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other Operating Systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

```

---

### Post by eternalsword on 2007-02-13
kernel 2.6.17.10 is still installed.  old kernels always remain even after updates.  this allows users to fall back to a stable environment if things go haywire.  if the new kernel is stable for your system, then you can safely remove the old kernel and grub will automatically remove that entry.  As a rule of thumb, however, I advise at least having one fallback kernel.  When another kernel comes out you can then remove the oldest.

---

### Post by chaplanger on 2007-02-13
Crooksey & eternalsword thanks for your input.  I have now edited GRUB and remarked the old kernel entries.

One last question: eteranlsword you advised to keep the old kernel which provided long term stability.  This makes sense.  As more kernels come out and are installed -- what steps are involved in removing the oldest kernel from the system?

Thanks again for your help!

---

### Post by Crooksey on 2007-02-13
ls /boot/vm*
rm <oldest kernel>

On a modern system its not going to make much difference removing them, i like to have two kernels, 1 kernel as the default, then one as a failsafe, recovery mode inst that great.

---

### Post by Brunellus on 2007-02-13
> **chaplanger said:**
> Crooksey & eternalsword thanks for your input.  I have now edited GRUB and remarked the old kernel entries.

One last question: eteranlsword you advised to keep the old kernel which provided long term stability.  This makes sense.  As more kernels come out and are installed -- what steps are involved in removing the oldest kernel from the system?

Thanks again for your help!
apt/synaptic will be the cleanest way of doing this.  simply remove the linux-image-generic package-2.6.x that you want to remove.  your /boot/grub/menu.lst will be updated automatically.

There was a time I kept a LOT of kernels handy when I was testing Dapper.  Good thing, too.

---

### Post by tonyr1988 on 2007-02-13
To move the old kernels, just go into Synaptic and remove linux-image-[kernel version]

As far as GRUB entries, I actually found something pretty cool a little while ago (I doubt I'm the first person to find it, but it was by pure accident :D). If you add a blank line into your GRUB menu, like:

> title
root

It will make everything below it invisible at first. For example, here's part of my menu.lst:

> title           Ubuntu Edgy 
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

title
root

title           Ubuntu Edgy (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

When I boot up, all I see in GRUB is:

> Ubuntu Edgy
Windows XP Professional

But...if I scroll down further, then the Ubuntu Edgy (recovery mode) appears. I don't know if it's a feature or a bug, but it's actually pretty cool - it keeps my GRUB menu nice and clean, but I can access recovery modes, old kernels, and memtests if I need to (which is a rarity).

Sorry for getting so far off-topic - just thought I'd share that little bit. :)

---

### Post by chaplanger on 2007-02-13
Thanks All!

It really is amazing how simple both computing and adjusting files are in Linux!

---

### Post by Brunellus on 2007-02-13
> **chaplanger said:**
> Thanks All!

It really is amazing how simple both computing and adjusting files are in Linux!
yeah.  Linux gives me back a computer with files I can read and learn from.  Windows took that away from me when they moved everything to the Registry.

---

### Post by uterrorista on 2007-02-17
relating to post number 1.
how can i see that? where is that file? i also want to put in comments some entries. 
thanks

---

### Post by spoot on 2007-02-17
> **uterrorista said:**
> relating to post number 1.
how can i see that? where is that file? i also want to put in comments some entries. 
thanks
This should be in the /boot/grub/menu.lst file.

---

### Post by uterrorista on 2007-02-18
thanks :KS :KS :KS :KS :KS

---

