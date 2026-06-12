---
title: "Totally newb with Ubuntu"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Rasalas on 2006-11-09
i would like to know of a program to handle partitions, or if anyone can help, i want to resize the partitions on the hard disk, i have dual boot Ubuntu as default and Windows as secondary, i would like it vice-versa, or just Windows, but i dont know how to do that.  the reason i would like to change to Windows is that I use the computer for entertainment and some other stuff i cant do with Ubuntu as I am now, dont flame me please.

---

### Post by ReaderRat on 2006-11-09
[**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)

---

### Post by bruenig on 2006-11-09
```
sudo apt-get install gparted
```
after installation it should be in the menus at system>administratin>GNOME Partition Editor I think. I use xubuntu but that is where it was on dapper.

---

### Post by xyz on 2006-11-09
Hi Rasalas,
[URL="http://en.wikipedia.org/wiki/GParted"]
Have a look at this: creating, destroying, resizing, moving, checking and copying partitions
[/URL]

---

### Post by devilsadvocate1987 on 2006-11-09
If you just want to change your default os to windows, all you need to do is to change the default in grub's menu.lst

you can find that in /boot/grub/menu.lst

If you need more details, ask for them. It could screw things up pretty bad if you dont do this right :)

---

### Post by Rasalas on 2006-11-10
thanks for the help guys, and yes please, can you give PM me or post more details for that, because i didnt understand much.

---

### Post by xyz on 2006-11-10
**This post is about making Windows your default OS at boot**
Go Application > Accessories > Terminal and type the following:
```
 sudo gedit /boot/grub/menu.lst

```
You will be asked for your password which you'll type in. Then a new "window" will open. You'll be now doing some editing in there so Windows will boot first.

Near the top of your menu.lst file, you'll see something like this: (it's the number you see next to 'defaut' that counts!)
> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
**default		6**

Why 6 and not 1 0r 5?
Now still in your menu.lst, scroll down till you see:
**End Default Options**
I'll now do a copy/paste of what I can read in mine:
> ## ## End Default Options ##

**0**title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda2 ro ro quiet splash elevator=cfq
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

**1**title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

**2**title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro ro quiet splash elevator=cfq
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

**3**title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot

**4**title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
**5**title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
**6**title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


You noticed **the numbers I added in bold next to "title"?**
You do not want these numbers in there; I just added them for the sake of explaining.

Now you need to go and count the same way I did above. And then depending on the number you will come up with, you'll need to change:
> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default X
the X and type in the number you came up with. Now "Save" your menu.lst

As you see, if I want Windows to boot first, I need to insert the number 6 in my menu.lst
What about you?
Hope this helps a bit.

---

### Post by Rasalas on 2006-11-10
ok, my number is 4, i type it in but when I restart my computer Ubuntu is still default.  do I have to do something else? i will paste what it says just in case.

> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 4

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
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
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

this is what it says do I have to add the X next to the number or that just represents the number I have to type in?

---

### Post by bulldog on 2006-11-10
Try 3 instead of 4.

---

### Post by Rasalas on 2006-11-10
it doesnt do anything different.

---

### Post by bulldog on 2006-11-10
Then you probably made a mistake.

Open your menu.lst```
gksudo gedit /boot/grub/menu.lst
```
Now alter this part```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```
And replace the 0 with a 3.
Save the file and reboot.

---

### Post by Rasalas on 2006-11-12
thanks for the help guys, i thought that i had to write default again, i fixed it and it works fine now, i appreciate your help.

---

