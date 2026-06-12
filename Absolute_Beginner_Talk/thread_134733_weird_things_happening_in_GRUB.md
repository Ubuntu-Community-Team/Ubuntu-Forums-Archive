---
title: "weird things happening in GRUB"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by candide on 2006-02-22
i am a dual boot machine. i just recently installed ubuntu.
when i booted up originally, i could choose ubuntu, ubuntu safe mode or windows XP.(3 choices)

NOW there are more choices! ubuntu kernel 2.6.12.10-386
and its safemode
AND ubuntu kernel 2.6.12.9-386 and its safemode
and XP still.(5 choices!!!)

why are more kernels, "boot choices" whatever you would call it showing up??

---

### Post by bluevoodoo1 on 2006-02-22
That's what happens when you update to a newer kernel. Did you do that recently? The extra listings are not something to be worried about. If you want to "get rid" of the other, older kernels, there are threads here about how to edit your grub menu.

---

### Post by pbaehr on 2006-02-22
The easiest way to remove the redundant entries from your grub menu is to edit /boot/grub/menu.lst and remove the old entries. You can also customize various other aspects of grub in this same config file if you're feeling adventurous.

---

### Post by candide on 2006-02-22
[QUOTE=pbaehr]The easiest way to remove the redundant entries from your grub menu is to edit /boot/grub/menu.lst and remove the old entries. [/QUOTE]

by "edit" do you mean i can just go down to "end default options" and delete a whole choice? 
.
.
.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd02)
kernel		/boot/vmlnuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot
.
.
.
this whole thing?

---

### Post by pbaehr on 2006-02-22
That's the ticket. Make note of which entries you want and delete anything you don't want from the bit under # End Default Options #. (That's actually a comment marking the end of the options above, but immediately following it is the part that defines the different OSes)

Just take out the whole entry: title, root, kernel, initrd, savedefault, boot, and any other lines that may be there. They should be pretty obviously seperated by a blank line if you haven't edited it yourself.

Do be careful, though, if you remove the ones you want you could end up with more trouble.

Sorry I wasn't more specific before.

---

