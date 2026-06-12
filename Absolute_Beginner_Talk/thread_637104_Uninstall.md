---
title: "Uninstall?"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by T-Fox on 2007-12-10
How do I go about removing Linux from my system? It's a great OS and everything, my parents kind-of got peeved. Anyways, can someone explain how to do this off of a Vista - Ubuntu Dual Boot System?

Thanks.

~T-Fox

---

### Post by kefurd06 on 2007-12-10
thing about that is, the grub (where u pick what to boot, ubuntu, vista, etc).. the grub info is stored on the linux partition (i think), so u can use livecd or anything u want to get rid of the linux partitions and resize vista partition to take up the recovered space, but then you won't be able to boot anything, b/c the grub loader is looking for the linux partition to get data on what/how to boot. there's all i know. 

anyone want to touch on what to do to get vista back on top?

---

### Post by T-Fox on 2007-12-10
Thanks for the help, but being able to continue to boot would be nice too. :)

---

### Post by Ub1476 on 2007-12-10
You can, of course, always "hide" Ubuntu:)

However, if you want to remove Ubuntu, first you need to reinstall its boot loader. Look at the last paragraph [here]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first").  When it's reinstalled (check by restarting), go into Vistas partition manager and delete Ubuntu from there.

---

### Post by kefurd06 on 2007-12-10
(in the interest of saving users time, i'm posting the last paragraph)

taken from [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

If instead of GRUB you want Vista's bootloader to be in charge, load up the Vista installation and install EasyBCD. Go to “Manage Bootloader”, then “Reinstall the Vista Bootloader”, an GRUB is overwritten. You can then configure the Vista bootloader to add Linux to the boot menu.

---

### Post by Calash on 2007-12-10
In XP you could just boot to the install CD, go to the command prompt, and type FIXMBR to get it to boot to the OS.

Not sure about Vista, but I would expect it to have a similar ability.

---

### Post by spiderbatdad on 2007-12-10
you can easily edit /boot/grub/menu.lst to boot vista by default

---

### Post by kefurd06 on 2007-12-10
> **Calash said:**
> In XP you could just boot to the install CD, go to the command prompt, and type FIXMBR to get it to boot to the OS.

Not sure about Vista, but I would expect it to have a similar ability.



you'd be surprised :) and besides, how many puters ship with a vista dvd? i'm going to guess zero.

---

### Post by Calash on 2007-12-10
Depends on where you buy it from.  They need to include some form of installation or recovery media since you purchased the licence.

I just confirmed that the Vista DVD has a similar option to boot and repair the MBR.  If you have a DVD you should be able to fix this with little problem.  If not there are some good options above :)

---

### Post by george34 on 2007-12-11
l would like to uninstall Ubuntu 7.04 . Sporting Windows XP .
How do l g about it ls ? Wll this operation rectify the partitions to their
original form?
Thanks in advance for replies

---

### Post by Computer Guru on 2007-12-14
> **kefurd06 said:**
> you'd be surprised :) and besides, how many puters ship with a vista dvd? i'm going to guess zero.

Actually, Microsoft has made a copy of the recovery disc available for free - it's hosted on the EasyBCD website and you can download it at: [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

