---
title: "[SOLVED] Grub,What did I do wrong?"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by mickey57 on 2007-11-29
....[SIZE="3"][COLOR="DarkRed"]Two seperate hard drives here.Gutsy is (0,0)[/COLOR][/SIZE]:confused:
[COLOR="DarkRed"][SIZE="3"]

Damn,I saw,Windows XP pro. in the
Grub options and thought I was home free.Didn't try to boot it until this morning to check it out.No go.Blank screen with a dash blinking,is all I got for the XP boot.
...../should I make the False to true in the first two codes shown here?[/SIZE][/COLOR]

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=704f316f-6ae0-4ca4-b1f4-87b2f4367426 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=704f316f-6ae0-4ca4-b1f4-87b2f4367426 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, kernel 2.6.20-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=704f316f-6ae0-4ca4-b1f4-87b2f4367426 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet

title Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=704f316f-6ae0-4ca4-b1f4-87b2f4367426 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title Microsoft Windows XP Professional
root (hd1,0)
save default
makeactive
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by philinux on 2007-11-29
This is what mine looks like


```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows 95/98/Me
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by mickey57 on 2007-11-29
.[COLOR="DarkRed"][SIZE="3"]...Uhmm.I will edit this and put it in.Can't hurt?????I know not to screw with the Ubuntu at all.I am even leery of going above it to make those up top true:lolflag:[/SIZE][/COLOR]


map		(hd0) (hd1)
map		(hd1) (hd0)

---

### Post by mickey57 on 2007-11-29
[COLOR="DarkRed"][SIZE="4"]...Thank You Phil.That did it:guitar:
.......Mickey[/SIZE][/COLOR]

---

### Post by philinux on 2007-11-29
Ok then, easy fix. Please mark the thread solved. Thread Tools pull down menu.

---

### Post by Matthew Bartram on 2007-11-29
The savedefault and updatedefault entry bits are only if you want GRUB to automatically change what default it boots to. (e.g. the last one booted)
If you've removed windows, and simply GRUB is left not knowing, all you need to do is remove the section:
```
title Microsoft Windows XP Professional
root (hd1,0)
save default
makeactive
chainloader +1
```
Then, if you want it to boot quicker, as Ubuntu does by default if it doesn't detect windows, you can change from further up: timeout 10 to timeout 3 (for example - that's just the seconds it waits in case you don't want the default) and unquote hiddenmenu (i.e. change #hiddenmenu to hiddenmenu), so if you actually want the menu, you have to press ESC within the 3 (or whatever seconds.)
So that section will look like:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

---

### Post by Matthew Bartram on 2007-11-29
Or did I misunderstand you? Are you upset that GRUB thinks Windows is there, or upset that Windows won't boot?

---

### Post by Matthew Bartram on 2007-11-29
Oops! didn't read carefully enough to realise you've already solved it!

---

### Post by Vixis on 2007-11-29
The problem was in:
```
title Microsoft Windows XP Professional
root (hd1,0)
**save default**
makeactive
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST

```

Must be one word, not two:
```
savedefault
```

---

### Post by mickey57 on 2007-11-29
> **Matthew Bartram said:**
> Oops! didn't read carefully enough to realise you've already solved it!
[SIZE="3"][COLOR="DarkRed"]**********************************
...Thanks for taking the time Matthew.I have had nothing but A1+ help form this community:mrgreen:
....I was fooling around with XP all day.Just trying to see exactly what I have on that disk.
......................Mickey
[/COLOR][/SIZE]

---

### Post by mickey57 on 2007-11-29
> **Vixis said:**
> The problem was in:
```
title Microsoft Windows XP Professional
root (hd1,0)
**save default**
makeactive
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST

```

Must be one word, not two:
```
savedefault
```
................**************.......................
[COLOR="DarkRed"][SIZE="3"]...No sir.The problem was exactly as Phil described.All I did was plug this in.[/SIZE][/COLOR]
map		(hd0) (hd1)
map		(hd1) (hd0)
[COLOR="DarkRed"][SIZE="4"]***************************************
Thankya,Thankya,thankya'll,as Gomer would say:guitar:
..............Mickey[/SIZE][/COLOR]

---

