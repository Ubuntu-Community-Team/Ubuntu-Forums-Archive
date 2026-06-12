---
title: "removing realtime kernel?"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by mrufino1 on 2007-10-31
Yesterday I decided to try installing ubuntu studio on my laptop, and decided that it is not for me right now because I don't have the desire to learn a bunch of new music programs when I already do plenty of work on windows (I love ubuntu for EVERYTHING else right now!). Anyway, the realtime kernel is now installed, and hibernate does not work, but it works fine if I boot into the t=regular 7.10 kernel. How do I remove ubuntu studio altogether? Is there a way to "roll back" ubuntu, like a "system restore" in windows? I loved the way ubuntu was running at 8pm yesterday and shouldn't have messed with it...I also installed some 32 bit libraries to try to get shockwave working and that didn't do anything, so I'm not sure if having those floating around unnecessarily does anything bad for the system. Anyway, the basic question is how to I "roll back" or uninstall the realtime kernel? Thanks.

---

### Post by HermanAB on 2007-10-31
The kernel is so small that there is not much point in deleting it.

Anyhoo, look at /boot/grub/menu.lst and delete the one you don't want or move the other one to the default position.  Do read the man page for the gory details!

---

### Post by mrufino1 on 2007-10-31
Aah, thank you. Moving the regular kernel to the default position is actually the better option I think, then if I ever want to use studio I'll still have it on there. Thanks, I'll try it now.

---

### Post by HermanAB on 2007-10-31
Read the grub man page though.  You somehow mark the one as the default - something about an asterisk or some such...

---

### Post by mrufino1 on 2007-10-31
Sorry, I'm back- do I cut and paste the one I want as default to the top of that list? I am not sure what I am looking at, and don't want to make my computer unbootable. Here is the pasted text of my list if that helps:


## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=4d2fbfab-b70d-4dad-be57-a10f266f3456 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=4d2fbfab-b70d-4dad-be57-a10f266f3456 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4d2fbfab-b70d-4dad-be57-a10f266f3456 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4d2fbfab-b70d-4dad-be57-a10f266f3456 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4d2fbfab-b70d-4dad-be57-a10f266f3456 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4d2fbfab-b70d-4dad-be57-a10f266f3456 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


So I would cut the 2 generic kernels and paste them above the realtime ones?

---

### Post by HermanAB on 2007-10-31
Here is the manual:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

The menu.lst file should have a line 'default 1' or some such.  The number is simply the position of the stanza for the kernel to load (starting from 0).  So if the one you want to run is the third from the top, then you could say 'default 2' and that will be the one that will run.

You can also specify the delay time and many other things.

Cheers,

Herman

---

### Post by mrufino1 on 2007-10-31
Okay, I changed it to default 2, which is the one I want. Now I am not able to save it because it says I don't have permission. How do I save it?

---

### Post by dcstar on 2007-10-31
> **mrufino1 said:**
> Okay, I changed it to default 2, which is the one I want. Now I am not able to save it because it says I don't have permission. How do I save it?

Open a terminal:
```
gksudo gedit /boot/grub/menu.lst
```
Change the default value to "saved", then it will be whatever you booted off.

---

### Post by mrufino1 on 2007-10-31
Cool, thanks, I figured it out, and it works fine after reboot. Thanks for the help!

---

