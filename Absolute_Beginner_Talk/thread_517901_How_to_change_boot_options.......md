---
title: "How to change boot options......"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by 12hello on 2007-08-05
hey guys i have been using ubuntu for quiet some time .. have got used to how things work ...
but my default os is ubuntu ..................................

which is something my family is not really comfortable with ......

can u tell me how do i make my default os xp ?????

heres hows my grub menu.lst looks like


//////////////////////////////////////////////////////////////////////////////////////////////////////

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f792b662-e3a5-45d2-a536-e5fe45e700fb ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f792b662-e3a5-45d2-a536-e5fe45e700fb ro single
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

//////////////////////////////////////////////////////////////////////////////////////////////////////////////

---

### Post by Campingman on 2007-08-05
All you need to know about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)
Hope this helps

---

### Post by dougfractal on 2007-08-05
normally  there's a "default 0"  near the top
change to
> default         4


or make 
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

the first entry

---

