---
title: "Editing GRUB Boot Options"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by karma on 2005-12-14
I am new to linux and just finished installing Ubuntu.

I have Windows XP and Ubuntu on the same HD.....and it both boots fine. Since I have to use most of the applicaitions in Windows, I want to make it boot into Windows automatically and boot Ubuntu only with manual actions.

Here is my default GRUB menu list:

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
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


```

Here is how I plan to edit it with cut and paste after logging in as root and opening the "menulist" from a window as I have no knowledge of using commands in the terminal window :confused:  .

Editing:
```

# memtest86=true

## ## End Default Options ##
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:Linux Ubuntu
root

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

```

Will opening it in an editor directly in a window and editing it work??

Did I edit the menulist correctly??

Thank you.

---

### Post by lreyes6 on 2005-12-14
hi
i did the same @ home... 
u just have to cut and paste the windows block (5 or 6 lines) to be the first option... you should backup your menu.lst first editing just in case something is missing...

---

### Post by karma on 2005-12-14
thank you

---

### Post by saltydog on 2005-12-14
Then run :
sudo update-grub

---

