---
title: "Weird Booting Problem"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by quandrum on 2007-05-31
I just installed Feisty Fawn and I am having an odd booting problem. I have 2 hard drives, a 200gb SATA with a windows partition and a 40gb IDE with Ubuntu installed on it. Grub was installed on the mbr of the SATA drive. 
Now, when I boot up normally, I get the grub menu, and Ubuntu boots up fine, but when I try to boot windows, it hangs at "Starting up...". If I boot from the Ubuntu livecd, and choose boot from the hard drive, I get the grub menu , but now both Ubuntu and Windows boots just fine. I was just wondering if anyone could clue me into what the livecd does that allows this to happen and any possible fixes.

menu.lst
> 
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=088de3c3-99ac-4386-a850-17efa0444bc9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=088de3c3-99ac-4386-a850-17efa0444bc9 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd1,0)
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
rootnoverify	(hd0,0)
savedefault
makeactive
map (hd1) (hd0)
map (hd0) (hd1)
chainloader	+1

---

### Post by bernied on 2007-05-31
Try removing the two map commands in the windows entry. Just comment them out with # then it's easy to put them back if you need to.

You can see what's going on at a grub command line. Just hit 'c' at the grub menu, then use tab completion to see what's what.

[This bit](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer) of Herman's web site might be helpful for you. Check out the rest of the page as well.

---

