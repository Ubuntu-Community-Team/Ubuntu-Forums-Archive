---
title: "GRUB customization?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by baba_oreilly on 2007-12-21
I enjoy playing around with Ubuntu a little bit, but for most tasks I use Windows. I installed Ubuntu as a dual-boot partition on my laptop, and GRUB defaults to sending me to the Ubuntu partition if I don't select windows in time. My question is, can I rearrange the order of the options in GRUB so if I don't press a key, it defaults to the Windows partition? Actually my dream scenario is that it automatically boots into Windows unless I hold down F8 or some key during boot-up, in which case it would send me to Ubuntu. Is that possible? Thanks for any help!

---

### Post by fain on 2007-12-21
yes in /boot/grub/menu.lst config file is your boot order. If you scroll to the bottom of that file you will see the boot configuration for grub in the same order as your boot screen is. You can set the default boot entry by setting the default option to the number starting from 0.

example of my menu.lst

```

default 4
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=08e45ba6-5d5f-4a33-9781-cd3d9f9401b0 ro quiet nosplash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=08e45ba6-5d5f-4a33-9781-cd3d9f9401b0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Wintendo64
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

the "default 4" would boot windoze first. because it starts from 0.
note the default should be at the top of your config and set to 0 already.

edit: For the record, I just wanted to note that MY menu.lst says "default 0" :) I just changed it for the example. Ubuntu ftw!!!!!

---

### Post by Partyboi2 on 2007-12-21
Yes you can arrange the order of grub so that it defaults to windows after a certain time.
For changing default o/s
[http://www.users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://www.users.bigpond.net.au/hermanzone/p15.htm#osprefernc) ( I used option 2)
To change the time before it defaults to windows
[http://www.users.bigpond.net.au/hermanzone/p15.htm#timer](http://www.users.bigpond.net.au/hermanzone/p15.htm#timer)
Not sure but maybe for your dream scenario you might be able to achieve that by using the hide menu option with grub.
[http://www.users.bigpond.net.au/hermanzone/p15.htm#hidethemenu](http://www.users.bigpond.net.au/hermanzone/p15.htm#hidethemenu)
If you get stuck post your /boot/grub/menu.lst
```
cat /boot/grub/menu.lst
``` 
and someone should be able to help.

---

### Post by rdoolen on 2007-12-21
Why isn't Windows "default 3"?

---

### Post by mmcmonster on 2007-12-21
Slot three happens to be:
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:root

```

It probably doesn't do anything. :-)

---

### Post by philinux on 2007-12-21
Another option is to install and run startupmanager from synaptic.

Nice gui for changing these settings.

---

### Post by baba_oreilly on 2007-12-21
Thanks for the responses folks - very helpful!

---

