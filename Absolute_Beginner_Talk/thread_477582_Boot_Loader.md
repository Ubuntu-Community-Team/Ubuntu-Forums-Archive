---
title: "Boot Loader"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by bill wray on 2007-06-18
When Grub starts, I am offred several operating systems to load, and there is a default OS which loads after 10 seconds, or so. Is there a way to change the order, or better yet, change the default system?

---

### Post by LaRoza on 2007-06-18
Yes

Goto Terminal: 
```

gksudo gedit /boot/grub/menu.lst

```
At the end of the file, most of it is comments, change the order of the entries, the Entire block.

You can see other options like "hidden menu", to hide the menu, and the automatic startup timer, which you can change easily

---

### Post by logos34 on 2007-06-18
> **bill wray said:**
> When Grub starts, I am offred several operating systems to load, and there is a default OS which loads after 10 seconds, or so. Is there a way to change the order, or better yet, change the default system?

The easiest way is simply to change the 'default' line near the top of menu.lst file to whatever entry you want to boot automatically (start counting with '0'):

**default   1**   (this boots the second kernel/title from the top on the menu screen)

**default   3**   (boots 4th entry down)

and so on.

---

### Post by davidwfox on 2007-06-18
Bill - hope you don't mind me joining your thread, but I have related issues and this seems to be a good place to raise them.

With the recent upgrade / update to the kernel my bootloader now shows 2.6.20-15 and 2.6.20-16, each of them with normal boot mode and recovery boot mode. I'm guessing that there's no longer any need for the two 2.6.20-15 entries to be there - how do I get rid of them, to reduce the number of items on the menu?

Secondly, I tried the terminal entry as advised by LaRoza and came up with:
(gedit:6049): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

A pop-up did appear however, entitled "menu.lst(/boot/brub) - gedit". At the end of a string of comment lines I have:
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=53e6fc67-eb66-4c1f-9275-4d6485d7d70e ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=53e6fc67-eb66-4c1f-9275-4d6485d7d70e ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=53e6fc67-eb66-4c1f-9275-4d6485d7d70e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=53e6fc67-eb66-4c1f-9275-4d6485d7d70e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

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

I can post the comment lines if they help.

How do I sort this out?

---

### Post by logos34 on 2007-06-18
davidwfox,

> (gedit:6049): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Just disregard.  It's normal.  You're extra safe if you open it with 'gksudo'.  (Try to avoid opening external applications from the terminal requiring superuser priviledges with just 'sudo'.  Better to use 'Run Application' gui.)


To hide those older kernels, just comment them out with a hash (#) mark thus:

> [COLOR="Blue"]#[/COLOR]title Ubuntu, kernel 2.6.20-15-generic
[COLOR="Blue"]#[/COLOR]root (hd0,6)
[COLOR="Blue"]#[/COLOR]kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=53e6fc67-eb66-4c1f-9275-4d6485d7d70e ro quiet splash
[COLOR="Blue"]#[/COLOR]initrd /boot/initrd.img-2.6.20-15-generic
[COLOR="Blue"]#[/COLOR]quiet
[COLOR="Blue"]#[/COLOR]savedefault

---

### Post by davidwfox on 2007-06-18
logos34 - many thanks - another satisfied customer!

The bean count's a giveaway that I'm a novice. I'm still trying to figure out what commands to use to open / edit what apps. I'm now a step further along the learning curve.

Bill - thanks for the use of your thread - maybe you've picked up a bit more useful info as well.

---

### Post by davidwfox on 2007-06-19
Bill - sorry to butt in again.

logos34 - could you perhaps have a look at my new thread: How to open/edit an internal/external application??  ([http://ubuntuforums.org/showthread.php?t=478097](http://ubuntuforums.org/showthread.php?t=478097))

---

### Post by glacierview on 2007-07-05
Hello I'm very new to this. I too got the warning, and a pop up window that was blank. where do I go from here.

---

### Post by jputman01 on 2007-07-05
> **glacierview said:**
> Hello I'm very new to this. I too got the warning, and a pop up window that was blank. where do I go from here.

like before you can ignore the warning, i the window that opened was blank you most likely misspelled something, try copying and pasting from the above post to make sure you get it correct

---

### Post by taikuodo on 2007-08-18
i tried default 3, and it could not boot xp right away. I have three linux things followed by a divider, then XP

So XP is the 4th one down, so it should be **default 3 right>?**

---

### Post by Paul133 on 2007-08-18
Actually, it probably counts the divider. Try 'default 4' and see where that gets you.

---

