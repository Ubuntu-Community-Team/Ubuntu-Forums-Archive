---
title: "Changing Boot Order?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by jmattos on 2007-03-19
Hi all

Can someone tell me how to change the boot order in GRUB? I created a dual boot configuration with Windows XP and Ubuntu 6.1

I'd like to change the boot order so that Windows XP is the default.. how do I do that?

Thanks!

---

### Post by toddhd on 2007-03-19
Look at the /boot/grub/menu.lst file. The comments in the file have lots of info. Probably the easiest way is to change "Defaut" value, near the top of the file. It is set to 0 initially, which means whatever is first in the list, is the default choice. If Windows is the 4th item in the list, then change Default to 4, and bingo, you are golden. There is also way to tag the default file using a name, which is better way to do it, since sometimes things like a Kernel upgrade can add more items to the menu list. But that will get you started.

PS - Guess I should add that edit the file, you should open up a terminal, and type:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by raymasky on 2007-03-27
I want vista to boot by default. I'm pasting my menu.lst file here. Could you tell me what will the value of default be for me  ?? Shoudl i change it to 3 ..or 4 ??


> 

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
boot

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





---

### Post by Musicalmidget on 2007-03-27
> **raymasky said:**
> I want vista to boot by default. I'm pasting my menu.lst file here. Could you tell me what will the value of default be for me  ?? Shoudl i change it to 3 ..or 4 ??

The value of default should be 4.

---

### Post by dpar on 2007-03-27
Correct me if I'm wrong, but I believe Linux starts counting at 0, so if your Vista is the fourth item on the list, the correct value should be 3.

---

### Post by Musicalmidget on 2007-03-27
> **dpar said:**
> Correct me if I'm wrong, but I believe Linux starts counting at 0, so if your Vista is the fourth item on the list, the correct value should be 3.

This is true, but I believe the "Other Operating Systems" divider in GRUB counts as another operating system, therefore taking the value of 3, and Vista subsequently taking the value of 4.  At least, that's what seems to happen on my system anyway.

---

### Post by Tomosaur on 2007-03-27
Check the link in my sig for a GUI method to playing with Grub :)

---

### Post by dpar on 2007-03-27
I also use Grubed now for that stuff. Makes life much easier:-D
By the way Musicalmidget, I just checked mine and you are right:)

---

### Post by raymasky on 2007-03-28
okay...i just updated ubuntu..n now the menu.lst file has changed .So now my default will have to be 6 right  ?? Another thing....Do i have to change the value each time there are changes to the kernel ?? why cant ubuntu just keep the latest kernel and delete the other boot options ?? Is there any way to do that  ?? Why is it repeated twice  ??

> 

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
boot

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




---

### Post by Tomosaur on 2007-03-28
@ Raymaysky -

By default, Grub will just list all of your available kernels. When you updated Ubuntu just now, you downloaded a newer kernel version. Pretty bad timing, I know! Anyway, you can tell Grub to show only your latest kernel version, although I personally prefer having it show two different versions. If you're like me and you mess around with stuff a lot - there's a chance (however small) that the latest kernel version may not work, or at least may not work as well as the old one. By having two kernels showing, it's a lot easier to just revert back to your older kernel if you have problems with the new one.

Anyway - to change how many kernels grub will show you, you need to edit your menu.lst file (surprise!). There is a line in there which says:
```

howmany=all

```
You should change the 'all' to however many kernels you want to see. For example, my line looks like:
```

howmany=2

```

Once you've done that, you may want to run the 'update-grub' command:
```

sudo update-grub

```

just to be sure that your changes are applied.

However, GrubEd will let you do all of this easily through a GUI. Link is in my sig if you want to check it out.

---

### Post by toddhd on 2007-03-28
If you want to set the Windows menu as the default, and not have to muck around with the list every time a kernel update occurs, then you need to use the savedefault option.

[http://www.gnu.org/software/grub/manual/grub.html#savedefault](http://www.gnu.org/software/grub/manual/grub.html#savedefault)

You simply change the defualt to "saved" instead of a num, then add the savedefault option to the menu item you want to be the default, in this case, Windows.

---

