---
title: "extra GRUB entries"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by xolot1 on 2006-06-24
i recently updated my kernel, for the little icon in the corner had popped up. now (since i dual boot with windows), i have an entry for the new kernel, and the old kernel in my GRUB selection list.  how can i get rid of the older one?

and a slightly separate question, is there a way i can rearrange the entries, in say the order:
ubuntu
windows
ubuntu recovery
windows recovery
etc?

---

### Post by scxtt on 2006-06-24
remove the "old" kernel, or just the entry?

and yeah, you can rearrange them any way you want - just move the text around ... (post your current menu.lst and i'll do it for you, if you want) ...

---

### Post by Kilz on 2006-06-24
[QUOTE=xolot1]i recently updated my kernel, for the little icon in the corner had popped up. now (since i dual boot with windows), i have an entry for the new kernel, and the old kernel in my GRUB selection list.  how can i get rid of the older one?

and a slightly separate question, is there a way i can rearrange the entries, in say the order:
ubuntu
windows
ubuntu recovery
windows recovery
etc?[/QUOTE]
The entries are in a file called menu.lst in /boot/grub you can edit it with```
sudo gedit /boot/grub/menu.lst
``` The sections should be near the bottom, and it is all sectioned off. You can edit the old ones out or move things around. But Beware! if you mess things up you may not be able to boot into ubuntu. If that happens have your install cd ready, it can reinstall grub for you.

---

### Post by user1397 on 2006-06-24
if you remove the old kernel from synaptic, they will be removed from the grub menu.lst file.

---

### Post by xolot1 on 2006-06-24
thank you very much.

ill just comment out the old kernel, and copy/paste to reorder (after backing up the file, of course).

---

### Post by xolot1 on 2006-06-24
does this appear safe?

```

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda5 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda5 ro single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin 
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title		Microsoft Windows XP Embedded
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

looks like it to me, but i just want to be sure.


and another question:

earlier in this file is an option for "pretty colors."
can i uncomment that? what kinds of modifications can i make?

---

### Post by scxtt on 2006-06-24
yeah, that looks good ...

here's my "pretty colors":
[indent]color red/black white/black[/indent]

---

