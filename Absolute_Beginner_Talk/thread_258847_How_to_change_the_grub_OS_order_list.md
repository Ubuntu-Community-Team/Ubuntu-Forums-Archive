---
title: "How to change the grub OS order list??"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by AlmaMater on 2006-09-16
Hey all

im very new to linux, i have a dual boot conf

win xp and Xubuntu

By default when i turn on the PC Ubuntu is selected... how can i make it to be win XP selected firt in the list by default??

i went to   /boot/grub/menu.lst

i know i have to change something in here.. but wehere : o ??
--------------------------------------------------------------------

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

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
---------------------------------------------------------------

thanks in advance

cheers :D

---

### Post by Klaidas on 2006-09-16
Here's a link: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

Hope this helps, 
Klaidas

---

### Post by someusernoob on 2006-09-16
```

gksudo gedit /boot/grub/menu.lst

```

On top you see the section 'default' which is set to 0 now. Change this 0 into 4, and XP will be the default selection of grub.

Why 4? Well, you start counting from 0.

So the Ubuntu options are 0 and 1 - memtest is 2 - the divider is 3 - and then Win XP is 4.

When there are more kernel options added, you might want to change the 4 to  whatever option XP is then by counting again.

---

### Post by lha on 2006-09-17
> **someusernoob said:**
> 
When there are more kernel options added, you might want to change the 4 to  whatever option XP is then by counting again.
Replace
```
# updatedefaultentry=false
```
with
```
# updatedefaultentry=true
```
to keep Windows as the default even when the number of kernels changes.

---

