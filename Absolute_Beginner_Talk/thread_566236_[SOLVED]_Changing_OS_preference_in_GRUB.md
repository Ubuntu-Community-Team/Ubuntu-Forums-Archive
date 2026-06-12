---
title: "[SOLVED] Changing OS preference in GRUB"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by BOZG on 2007-10-03
I currently have a dual partition for Windows and Ubuntu on my main PC.  When the GRUB loader boots, it normally loads Ubuntu as the preferential OS but how can I change this to boot Windows as my preferential OS?

I run Ubuntu only on my older PC and use that for practice until I get more accustomed to it but predominantly use Windows at the moment and it's a pain in the **** when I forget to scroll to Windows and have to reboot when it automatically goes into Ubuntu.

I know how to get into the editing list but I'm not sure how to change it.

Thanks.

---

### Post by alienexplorers on 2007-10-03
Change the number listed at the end of this section to the new section you want to boot.  You have to go to the end of menu.lst and count down starting at 0 till you get to the OS you want to boot.
> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0


The default is zero.  This has to be changed.

---

### Post by forestpixie on 2007-10-03
you need to change menu.lst, open it to edit

```
gksudo gedit /boot/grub/menu.lst
```

near the top you'll find this section

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		[COLOR="Red"]0[/COLOR]

it's this number which sets the default - counting from the first uncommented 'title' - count from zero till you reach the entry you want to be default - change the default and save, should be fine next time.

as an example what follows is my menu.lst - I have 3 lots of gutsy before I reach Feisty - I have my default set to 8, hope that helps


> title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=94ab3256-dde7-4e68-a209-56047a3c68a0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=94ab3256-dde7-4e68-a209-56047a3c68a0 ro single
initrd		/boot/initrd.img-2.6.22-12-generic

title		Ubuntu gutsy (development branch), kernel 2.6.22-11-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-11-generic root=UUID=94ab3256-dde7-4e68-a209-56047a3c68a0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-11-generic
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.22-11-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-11-generic root=UUID=94ab3256-dde7-4e68-a209-56047a3c68a0 ro single
initrd		/boot/initrd.img-2.6.22-11-generic

title		Ubuntu gutsy (development branch), kernel 2.6.22-10-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=94ab3256-dde7-4e68-a209-56047a3c68a0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-10-generic
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.22-10-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=94ab3256-dde7-4e68-a209-56047a3c68a0 ro single
initrd		/boot/initrd.img-2.6.22-10-generic

title		Ubuntu gutsy (development branch), memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Feisty Ubuntu, kernel 2.6.20-16-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9be84c49-0750-4aae-844b-4053af769e12 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


Edit - as has been said  already :)

---

### Post by BOZG on 2007-10-03
There a few titles with savedefault though?

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d95caed9-7ff7-4ebd-8a2c-46f3cbe467f7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d95caed9-7ff7-4ebd-8a2c-46f3cbe467f7 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d95caed9-7ff7-4ebd-8a2c-46f3cbe467f7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d95caed9-7ff7-4ebd-8a2c-46f3cbe467f7 ro single
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
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by forestpixie on 2007-10-03
counting the lines that start with title - assuming thats all the options in your menu - the number you need should be 6

---

### Post by BOZG on 2007-10-03
But where do I put in the 6?

---

### Post by drf_av on 2007-10-03
If you don't like menu.lst try using startupmanager.

---

### Post by BOZG on 2007-10-03
Yeah, SUM worked fine.  Thanks.

It was only after I'd actually rebooted with SUM that I realised where I was supposed to put in the 6. 

Thanks everyone anyway.

---

