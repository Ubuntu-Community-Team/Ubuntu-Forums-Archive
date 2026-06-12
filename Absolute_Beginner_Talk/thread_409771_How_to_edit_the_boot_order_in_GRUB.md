---
title: "How to edit the boot order in GRUB"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by oddcarout on 2007-04-14
Please help me I need to change the boot order of GRUB for my wife so that she can automatically boot to windows.

please let me know how.

I thought that I would need to edit my grub.conf file but can't find it.

TnA
Z

---

### Post by taurus on 2007-04-14
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
Change the

```
default     0
```
to whatever the value for the entry for Windows.  Remember, you count from 0 with the first entry and 1 with the second entry and so on.

Windows probably is the fifth entry so the value should be 4 then.

---

### Post by dreadlord_chris on 2007-04-17
what taurus said is true - except, and this is important, you need to count *each line that begins with **title*** as 1, still starting at 0.

i.e. (taken from my menu.lst)
```

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0e5f3819-6f12-49bd-9e82-904ff9e0fa54 ro vga=792 splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0e5f3819-6f12-49bd-9e82-904ff9e0fa54 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.20-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=0e5f3819-6f12-49bd-9e82-904ff9e0fa54 ro vga=792 splash
initrd		/boot/initrd.img-2.6.20-14-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=0e5f3819-6f12-49bd-9e82-904ff9e0fa54 ro single
initrd		/boot/initrd.img-2.6.20-14-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title         Windows 95/98/NT/2000
root          (hd0,0)
makeactive
chainloader   +1

```

Note that there are 7 lines that begin with **title**. So, if I wanted to set Windows as the default, I would set **default    6** (remember, count from 0).

This will work fine, until the kernel gets updated. You see, by default, new kernels are simply added to the beginning of the GRUB list. With **default** set to 0 this works fine - the new kernel always ends up being the default. Trying to default to the last item in an increasing list becomes problematic though.

One way to deal with this, and has the side-effect of keeping your GRUB menu from growing too long, is to change for another option in _menu.lst_. Look for this section:
```

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

```
The default is *# howmany=all*. This means each new kernel is just _added_ to the beginning of the list. I find it useful to change it to **# howmany=2**. This way only the 2 most recent kernels are kept in the GRUB menu. Also, this way, your Windows boot option will always stay the same.

Hope that's not too confusing :D

---

