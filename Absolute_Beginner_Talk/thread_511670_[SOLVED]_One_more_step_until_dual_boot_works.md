---
title: "[SOLVED] One more step until dual boot works"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by cptInsane0 on 2007-07-28
Ok, I have been working on this for a week. If you read the other threads I started, you can get the background info.  Anyway, I finally have things mostly setup. xp and linux are both on my first sata drive, which is technically my third drive since I have two IDEs.  When I installed grub to HD2, the boot loader starts, but then it wouldn't load ubuntu or windows.  Someone in the other thread told me to hit e to edit grub, change root from hd2 to hd0, and the boot it.  It went right in.  I then did sudo gedit /boot/grub/menu.lst and saved the changes.  I can get into ubuntu every time now.  However, I still can't get into windows, and I'm almost positive I didn't hose the installation, it just cant find NTLDR.  I changed the root for it to hd0,0, even though its on hd2 with ubuntu, i figured id need to keep it uniform.  there is also some code under that that says 
map (hd2) (hd0)
map (hd0) (hd2)

do I need to mess with those too?  Here is my menu.lst:


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fcb59298-99dc-43c5-bef4-0faca890e082 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fcb59298-99dc-43c5-bef4-0faca890e082 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fcb59298-99dc-43c5-bef4-0faca890e082 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fcb59298-99dc-43c5-bef4-0faca890e082 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
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

map		(hd2) (hd0)
map		(hd0) (hd2)
chainloader	+1

---

### Post by logos34 on 2007-07-28
You don't need the map lines if XP is on the same physical disk.  If windows is the first partition (sda1), then just this should do:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1


---

### Post by cptInsane0 on 2007-07-28
That did it!!! Thanks a lot. This whole thing has been a bitch.  I still have a lot to do with configuration, but this has been a good learning experience!

---

### Post by logos34 on 2007-07-28
> **cptInsane0 said:**
> That did it!!! Thanks a lot. This whole thing has been a bitch.  I still have a lot to do with configuration, but this has been a good learning experience!

Glad to hear it's working now.  Good luck!

---

