---
title: "Grub Doesn't Recognize Vista after installing ubuntu"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by rpzatkof on 2008-01-22
I had vista on one partition and created a new 20 GB partition for Ubuntu

I installed Ubuntu on the partition and ubuntu now runs and works and recognizes that there is 20GB's on its partition


it also recognizes the 2 GB recovery partition from vista - but not the 130 GB's that are missing from the hard drive

upon restart though it boots straight to ubuntu and has no option in the menu for vista

when the vista installation cd is put in it says it cannot read from the hard drive if we try to re-install vista

---

### Post by roboxking on 2008-01-22
I'm rather new when it comes to the grub, but I have a solution that might work. First of all, download GParted, the partitioning software, once you do, go to System-->Administration-->Partition Editor. If you can recognize your Vista Partition then look at the area name, (Ex. /dev/sda, /dev/sdb, etc) Then, if you can find it and correctly label it, go to Places-->Computer-->FIle System-->Boot-->Grub-->Device.map. You should see a list of things, something as this, 

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

if your device label isn't there, add it in like this

(hd(x))  /dev/sd(x)

Then save it. Oh and Another thing, you not only need the sd-whatever, but the number of the actual boot partition. Like, the main Vista partition. Then, back in the Grub folder, open menu.list. Scroll all the way down, and you should see something like this 

title		Ubuntu 7.10, Gusty Gibbon
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b98c44cf-3a0a-4aa0-9100-fdd04afc6865 ro quiet verbose
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, Gusty Gibbon (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b98c44cf-3a0a-4aa0-9100-fdd04afc6865 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Main Hard Drive:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

Now, if you don't see that last part about Windows, then add it like mine (but of course change the title, the hd (as defined by the previous file) and in the # section, make sure the device number matches) Then restart, and try it again, if it doesn't work, then change that last number in the root area, (the second number, for example in mine, it's (hd0,1) change the 1 area) If all else fails, then I would consult reinstalling Vista, or getting a separate hard drive for Linux/Vista

---

