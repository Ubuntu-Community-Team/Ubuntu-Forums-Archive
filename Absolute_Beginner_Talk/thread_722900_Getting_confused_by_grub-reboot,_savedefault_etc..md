---
title: "Getting confused by grub-reboot, savedefault etc."
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by alexforcefive on 2008-03-12
Hi guys

Basically I wrote this tiny script to reboot from linux straight to windows:

```
#!/bin/bash
sudo grub-reboot 4
```

(told you it was tiny). Anyway, it works fine but after I use it, windows becomes my default option in grub! I've read a bunch of vague posts from a year or two ago that insinuate the **savedefault --once** option might be broken in Ubuntu, but I was wondering if anyone had any extra information. I'll post the parts I think are relevant from my /boot/grub/menu.lst just in case. If you need any more information let me know

```
default		saved

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=true

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bf96faea-0e3e-45e9-b0ce-47d08f22cadc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
savedefault

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bf96faea-0e3e-45e9-b0ce-47d08f22cadc ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1

```

I'd appreciate any advice you can give. thanks!

---

### Post by terto on 2008-03-13
Hey, sorry to hear about your problem.

Have you already tried setting the default to *0* instead of *saved*? That is, making your Ubuntu entry  the default in every boot, except when you use your script of course.

Cheers.

---

### Post by alexforcefive on 2008-03-13
Yeah, if you change **default** it just ignores the savedefault option, so grub-reboot doesn't work at all :( Thanks though

It seems like savedefault in this version of grub is broken :( Hey, would it be really hard to switch to lilo? *edit* or downgrade?

---

### Post by terto on 2008-03-14
I think I've got it, keep your config file as you have it and add a line like this:
```
savedefault 0
``` to your windows entry.

If I understand correctly, grub-reboot overrides the contents of the *saved* field. You just have to override it back when grub is about to boot windows.

Please do tell me if this works for you, I don't have a windows partition to test it.

Cheers.

---

### Post by alexforcefive on 2008-03-14
Yeah, it doesn't work. It just boots whatever you set default to :(

Seems like this feature is just downright broken. Oh well, maybe I'll try to figure out how to switch to lilo

---

### Post by maniac_X on 2008-03-14
You might need to make 2 changes:

first where it says
```
default   saved
``` 

comment it out:
```
# default   saved
```

and then change where it says
```
savedefault
```
to
```
savedefault=false
```

---

