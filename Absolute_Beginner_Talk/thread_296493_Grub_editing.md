---
title: "Grub editing"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by IanGB on 2006-11-09
Hi Steve.

Although I did follow the link you gave and tried I could not change the menu.lst in Grub/Boot because of permission bans, so after a search I found this advice at [www.psychocats.net](www.psychocats.net)

for ubuntu press Alt-F2 and type gksudo nautilus and use the new desktop that opens to find the file and open it for editing.

I did this and successfully removed the three entries for abortive bistro loads, that I made before the current success with Dapper Drake, but now I do not know how to make the XP load before the Ubuntu which is what my wife would like to happen for her. Can anyone please detail the change needed to the set up below.

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Ian:D

---

### Post by localuser on 2006-11-09
> how to make the XP load before the Ubuntu

Either change the order of the entries, or change the "default" value at the top of the file.

Count starting from 0, so default 0 means the first entry will be the default.

---

### Post by brundles on 2006-11-09
You haven't included the whole menu.lst file but in short GRUB will default to whatever value is entered against the **default** line in menu.lst.

This can be either a number or **saved** in which case it reads it from the default file in /boot/grub. You can also update the value in that file using the grub-set-default command.

Lastly you can tell GRUB to change the default as one of the actions on a specific boot sequence:
```
title           Microsoft Windows XP Home Edition
root            (hd0,1)
**savedefault 0**
makeactive
chainloader     +1
```

That example from my menu.lst file means that whenever I boot to Windows it will always boot back to Ubuntu on the next restart.

---

### Post by BLTicklemonster on 2006-11-09
You can't just open a terminal and type, 

sudo gedit /boot/grub/sources.lst?

Looking at your list, xp is listed 7th, so counting from zero, it would be six. ( every time you see "title") So default would be 6. Timeout sec set to 3 gives you 3 seconds to press esc so you can see the boot menu in case you want to boot to ubuntu, and hiddenmenu hides the boot menu so you don't hardly know it happens...

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

This way, your wife can just sit back and let it boot without touching a thing. And if you want to boot, just press esc when you see the message pop up on the bottom of your screen prompting you to. 

I'm pretty sure I'm right in saying you should boot to 6. If not, the boot menu will come up like always... :)

---

