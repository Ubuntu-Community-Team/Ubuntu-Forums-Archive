---
title: "Errors on bootable CDs / Live CDs"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by rennen01 on 2007-03-19
I was trying to check out Fiesty and right after I checked the CD for defects, I got this error:

```
/bin/sh: can't access tty; job control turned off
```

Here is the output of my Grub Menu:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(**[B][COLOR="Red"]hd0,2[/COLOR]**[/B])
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(**[COLOR="Red"]hd0,2[/COLOR]**)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(**[COLOR="Red"]hd0,2[/COLOR]**)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		([COLOR="Red"]**hd0,2**[/COLOR])
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		([COLOR="Red"]**hd0,2**[/COLOR])
kernel		/boot/memtest86+.bin
quiet
boot

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
```

Does it look ok?

I have read that this error may possibly be caused by a Video Driver of some sort.  I will attempt to reboot and I hope it doesn't happen again :( 

If anyone knows the solution, please help.

Thanks in advance.

---

### Post by mykalreborn on 2007-03-19
well, feisty is still alpha now. i tried installing it yesterday, but the installer stopped in the middle of the process... my advice to you, if you want to install feisty is to install edgy eft and then upgrade to fesity with the alternate cd. it worked for me anyways. it takes quite some time, it's true, but you won't have to worry about faulty cd images. ;)

---

### Post by rennen01 on 2007-03-19
I meant any Live CD.  Sabayon, Mandriva, eLive just to name a few,  That is why I think it is Grub.

---

### Post by mykalreborn on 2007-03-19
> I meant any Live CD. Sabayon, Mandriva, eLive just to name a few, That is why I think it is Grub.

bummer dude. i'm afraid i can't help you. :(

---

### Post by rennen01 on 2007-03-19
Bump

---

### Post by rennen01 on 2007-03-19
So, apparently I can install from CD just not Live CDs.  Just got done installing Debian Etch.  :(

---

