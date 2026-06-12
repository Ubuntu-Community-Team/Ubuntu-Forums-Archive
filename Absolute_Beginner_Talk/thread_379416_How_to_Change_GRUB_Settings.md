---
title: "How to Change GRUB Settings???"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by lunchbox_1973 on 2007-03-08
Hi, how do I change the list in GRUB to have Windows the default OS to load instead of Ubuntu if I don't select anything? Thanks.

---

### Post by dstew on 2007-03-08
Edit the grub menu.lst file found in /boot/grub directory. Change the line "default = 0" to "default = x", where x is the list entry for your Windows OS. Grub counts starting at 0, so if Windows is the fifth item in the list, x would be 4. Also, you may need to comment out the "savedefault" line under the linux items, because this makes that item the default if you choose it later.

---

### Post by raja on 2007-03-08
You have to edit the menu in grub. So open it with your favorite text editor ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lstbkup
sudo gedit /boot/grub/menu.lst
```. You will see the list of boot options like this example from my menu ```
default		0
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,7)
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
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

The default number indicates the option that will be chosen by default. '0' here means the first option. In this example windows is the sixth option, so I would have to change the default to '5'. Make a backup of your menu.lst first just in case you have to revert to it.

---

### Post by Cobikegeek on 2007-03-08
You need to edit /boot/grub/menu.lst and change the default number (probably 0 now) to the number that corresponds to the which menu choice loads windows.  Don't forget that the menu choices are numbered starting with 0  (first choice is 0, second is 1.......)

Assuming you are using Ubuntu, In the terminal type the next line:

gksudo gedit /boot/grub/menu.lst

Enter your password and the editor should open menu.lst

Count the menu items starting with 0 to determine which menu item is windows and replace the current default number with that number.  The Menu list is near the end of the file.  The code for "default" is usually near the beginning of the file (instructions are there too).  Click save and that's it.

For example, my system has the Ubuntu kernel first (0), then the recovery kernel option (1) , then the memtest option (2) and then windows (3).  So I would enter

default     3

to make windows the default.  

If you ever do a kernel upgrade you might have to repeat this process since more items are added to the menu list and your windows item might not be the same number.

---

### Post by lunchbox_1973 on 2007-03-08
Thanks a lot guys. I'll give it a whirl, doesn't look too hard.

LB

---

### Post by bichopro on 2007-03-08
try too Grubed

[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

---

