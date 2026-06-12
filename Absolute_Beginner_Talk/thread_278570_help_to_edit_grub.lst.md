---
title: "help to edit grub.lst"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by pregoeater on 2006-10-16
im about to edit my grb.lst but before i do that i have a few question when i first instaled ubuntu it give me 3 choices unbuntu,ubuntu revory mode, and memtest. then win xp then next time i did a reboot it added two more that look like the first 2. would anyone recomend deleting them or should i keep then all or can i just REM them? what i would like to do is set it up so there are two thing on the list xp and ubuntu and shorten them time before it selects the os but if i ever need the recovery mode can i still use it if its off the list...here is my list file
```
## ## End Default Options ##

title        Ubuntu, kernel 2.6.15-27-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-27-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-27-386
boot

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

also i see that i can use # or ## and it says true or false what does that mean? any help would  would be great i think i know what to do and how to do it but i dont want to kill anything.



thanks
pre

---

### Post by taurus on 2006-10-16
The first one is your latest kernel so you want to keep that.  The next entry is the recovery mode using the latest kernel so you want to keep that as well in case you need to boot your machine into recovery mode.  The third entry is your old kernel so you want to keep that in case there is something wrong with the new kernel.  Then, you can remove everything else after that except your XP...  To edit your /boot/grub/menu.lst, open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by aysiu on 2006-10-16
As long as you back up the file first ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
``` and you have live CD, you can do whatever you want to the entries.

---

### Post by jordanmthomas on 2006-10-16
If a line has a # at the front of it, then GRUB ignores it.  This is called a comment.  If someone tells you to comment something out, you just put a # there.

Instead of removing the entries you don't need, might I suggest commenting them out?  That way, if you need them again, you can just uncomment them and they will be back.

What are you talking about when you say true / false?  If you are referring this line
```
# memtest86=true
```
I think it means "when updating GRUB, should I include memtest entries?

**wow, I got beat twice.

---

### Post by pregoeater on 2006-10-16
great so i will just # everything but ubuntu and xp what about changing the time it takes to auto pick the os?

---

### Post by elchinovi on 2006-10-16
> **pregoeater said:**
> great so i will just # everything but ubuntu and xp what about changing the time it takes to auto pick the os?

It's listed before the example that you gave.
it says

IE: "Timeout 10"

10 being the seconds, so you can put 15 sec, or how many seconds you want/need.
:mrgreen:

I'm working now, so I don't have a menu.lst to copy from. I'm sorry.

---

### Post by bulldog on 2006-10-16
Edit this in menu.lst,

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

Where you can alter 10 to what you want,but don't set it to zero [0] because you can't choose anything anymore.:D

---

### Post by pregoeater on 2006-10-16
have it just the way i want thanks for all your help


thanks 
pre

---

### Post by Tomosaur on 2006-10-16
You may like to take a look at the link in my sig :)

</shameless self-promotion>

---

### Post by elchinovi on 2006-10-16
> **pregoeater said:**
> have it just the way i want thanks for all your help


thanks 
pre

Glad to give back to the comunity!
Thank you!
:mrgreen:

---

### Post by PriceChild on 2006-10-16
If i were you, instead of removing them from the grub menu.lst, i would uninstall them:

```
sudo aptitude remove linux-image-whatever-versionp
```

---

### Post by bulldog on 2006-10-16
> **PriceChild said:**
> If i were you, instead of removing them from the grub menu.lst, i would uninstall them:

```
sudo aptitude remove linux-image-whatever-versionp
```

Don't know if that's a wise decision...........I like to have a kernel for safety reasons,when things go bad.

If you have more than two different working kernels,yes,you can uninstall some.

---

