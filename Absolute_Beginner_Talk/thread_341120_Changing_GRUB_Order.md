---
title: "Changing GRUB Order"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by icio on 2007-01-18
I've just installed Ubuntu onto my computer with dual-boot Windows XP.

I'm wanting to change the boot order of GRUB so that if I don't press anything Windows XP will load instead of Ubuntu. This is because my girlfriend uses this computer and may struggle with linux.

A quick search on google lead me to the file: /boot/grub/menu.lst
The part of the file that I am looking at is:
```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=bd0d60c2-8345-4a45-be96-dfaa70268f34 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=bd0d60c2-8345-4a45-be96-dfaa70268f34 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=bd0d60c2-8345-4a45-be96-dfaa70268f34 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=bd0d60c2-8345-4a45-be96-dfaa70268f34 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=bd0d60c2-8345-4a45-be96-dfaa70268f34 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=bd0d60c2-8345-4a45-be96-dfaa70268f34 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Win XP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Just before I change anything, I want to confirm that moving the section of the file for Windows XP
```
title		Win XP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
to the top of the list will not break anything.

Just wanting to be sure,
Thanks.

---

### Post by amo-ej1 on 2007-01-18
you might want to use the default directive

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.

```

simply enter 'default 4' to launch the 5th (numbering starts at 0) entry in the grub menu, also moving them up won't break anything

---

### Post by mcduck on 2007-01-18
> **amo-ej1 said:**
> you might want to use the default directive

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.

```

simply enter 'default 4' to launch the 5th (numbering starts at 0) entry in the grub menu, also moving them up won't break anything

Actually moving the entries *can* break things on the next update, if the moving is not done in the right way. Everything between the automagick kernel lines will just disappear when kernel update recreates the boot options..

Anyway, using the 'default' line is the good way to do it.

---

### Post by icio on 2007-01-18
Thanks guys, I'll go with the `default` option.

Also, could somebody explain what menu.lst mentions about "default saved" and "savedefault" is it saying that if you set "default saved" and then you choose an option with "savedefault" then it will start up with that next time?

---

### Post by bugster on 2007-01-18
I had the same issue when I started with Edgy just over a week ago and the link below helpedme no end.

[http://www.ubuntuforums.org/showthread.php?t=335696](http://www.ubuntuforums.org/showthread.php?t=335696)

---

### Post by mcduck on 2007-01-18
> **icio said:**
> Thanks guys, I'll go with the `default` option.

Also, could somebody explain what menu.lst mentions about "default saved" and "savedefault" is it saying that if you set "default saved" and then you choose an option with "savedefault" then it will start up with that next time?

It means that if you boot to Ubuntu, on the next boot Ubuntu is considered the default option and if you do nothing your computer will automatically boot to Ubuntu again. And if you boot to windows then Windows becomes the default option.. So the last used OS is the default on the next boot.

---

### Post by Tomosaur on 2007-01-18
Changing the actual order is not recommended, you're supposed to change the 'default' OS. The menu.lst is commented, which makes it very understandable so this operation is easy to do.

However, click the link in my sig if you don't want to edit the menu.lst file manually.

---

### Post by jhenager on 2007-01-18
Tomosaur is right. GrubEd is the easiest way to do it. Great program.

---

