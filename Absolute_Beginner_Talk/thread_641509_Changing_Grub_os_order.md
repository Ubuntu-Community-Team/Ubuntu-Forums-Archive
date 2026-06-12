---
title: "Changing Grub os order"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by kool_kat_os on 2007-12-15
On grub there is 4 OS's to boot from. How do I make it so that the default highlighted entry is Windows XP Media Center edition instead of Ubuntu when I turn on my computer.

Here is some info that might help: 
[HTML]title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f37035ca-4e6a-4ec2-88d7-e9afd695491b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f37035ca-4e6a-4ec2-88d7-e9afd695491b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/HTML]

---

### Post by kool_kat_os on 2007-12-15
Anybody???

---

### Post by overdrank on 2007-12-15
Hi and I believe this link will help
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by rsambuca on 2007-12-15
You have to edit your menu.lst and change the line that says

default  0

And please wait a day or two before bumping your threads.  If you require immediate help try the IRC channels.

---

### Post by kool_kat_os on 2007-12-15
So whould I change this line :

[HTML]default		0[/HTML]

to this?:

[HTML]default		5[/HTML]

???

---

### Post by overdrank on 2007-12-15
> **kool_kat_os said:**
> So whould I change this line :

[HTML]default		0[/HTML]

to this?:

[HTML]default		5[/HTML]

???

Yes that would be my understanding. :KS

---

### Post by Brindled on 2007-12-15
yep, 5 for your case.

---

### Post by kool_kat_os on 2007-12-15
Thanks, I tried it and it worked.

---

### Post by rsambuca on 2007-12-15
NO.  You want to set it at number 4 (depending on which Windows you want to run).  Counting starts at zero and includes all of the title and root lines.
You might just want to move the entire Windows entry to the top above the section that says

### BEGIN AUTOMAGIC KERNELS LIST

and keep the default a zero.  This way you won't have to mess around with it when the kernel is updated.

---

### Post by kool_kat_os on 2007-12-15
> NO. You want to set it at number 4 (depending on which Windows you want to run). Counting starts at zero and includes all of the title and root lines.
You might just want to move the entire Windows entry to the top above the section that says

### BEGIN AUTOMAGIC KERNELS LIST

and keep the default a zero. This way you won't have to mess around with it when the kernel is updated. 

I already changed it to 5 and it worked fine, do I still need to do that?

---

### Post by rsambuca on 2007-12-15
> **kool_kat_os said:**
> I already changed it to 5 and it worked fine, do I still need to do that?

No, you don't have to by any means.  I just presented it as an alternative.  If Ubuntu updates the kernel later, then the new kernel entries will appear in the menu, so entry number 5 will no longer be Windows.  If you move Windows to the top above the Automagic section, then it will still be the correct default number, and you won't have to keep editing your grub entries.

---

### Post by kool_kat_os on 2007-12-15
Thanks

---

