---
title: "Second Kernel appeared in Grub"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by ident4 on 2007-06-24
Hi

I haven't used Ubuntu for a while. When I started it up tonight it installed a lot of updates and after I rebooted it has Ubuntu listed twice (4 times if you include the recovery option)

I've got:

```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=82f1bf07-471a-4ab7-85d6-91a68af1d53f ro quiet splash live acpi=off
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=82f1bf07-471a-4ab7-85d6-91a68af1d53f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=82f1bf07-471a-4ab7-85d6-91a68af1d53f ro quiet splash live acpi=off
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=82f1bf07-471a-4ab7-85d6-91a68af1d53f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

From other threads I've found here on the subject, it seems that it would be Ok to remove 2.6.20-15. But when I do a search in Synaptic for "2.6.20-15" there's a lot of stuff there. 

Can someone tell this newbie _exactly_ how to remove 2.6.20-15?
I really don't just want to tick anything that has 2.6.20-15 for removal when I'm not sure what I'm doing

Many thanks

---

### Post by krul on 2007-06-24
if you are not sure...just don't remove anything. why bothering? You can eventually remove the entries in grub (the start up/boot menu).

---

### Post by BobCFC on 2007-06-24
If you want to just tidy up the menu you can comment out lines by putting # at the beginning.

That way you can always go back and uncomment them.. using the liveCD if necessary

You can see they are in little groups just be sensible and comment out a whole block without straggling lines.

Remember you must be root to edit the file such as
```

sudo gedit /boot/grub/menu.lst
```

---

### Post by ident4 on 2007-06-24
Many thanks

I have commented out the earlier kernel in Grub

:)

---

