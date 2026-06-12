---
title: "Problem..."
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Ronin_301 on 2007-06-17
I've talked to a friend who has used Ubuntu for awhile, and he has no idea what the problem here could be, so I figured I'd post it on here.

While using Ubuntu, it will occasionally, and completely randomly, give me a blank screen...all my programs are still running (can still hear music) but the screen shuts off as if it's gone into some kind of sleep mode (power indicator on the monitor flashes). There doesn't seem to be any rhyme or reason as to why it does this. Anyone have any ideas? I'm running an ATI Radeon 9200+ card if that makes any difference.

---

### Post by kevinlyfellow on 2007-06-17
Welcome to the forums!

I'm afraid it could be the graphics card.  Ati is not held in high esteem in the Linux world...

But, just to make sure its not a power management malfunction, try changing grub to boot without acpi.

```
gksudo gedit /boot/grub/menu.lst
```
and just put "pci=noapci" at the end of the line that starts with kernel.  For instance:
```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ab5fd55d-b3a3-473e-b395-49fa9af2e210 ro quiet splash [COLOR="Red"]pci=noacpi[/COLOR]
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

and reboot.  If this doesn't solve your problem, just remove the "pci=noacpi" option

---

### Post by benanzo on 2007-06-17
does anything happen when you move the mouse or tap the keyboard?  GNOME's default action is to go to a blank screen after a period of time as the screensaver.  Moving the mouse or tapping to keyboard is supposed to wake it up.

---

### Post by Ronin_301 on 2007-06-17
> **benanzo said:**
> does anything happen when you move the mouse or tap the keyboard?  GNOME's default action is to go to a blank screen after a period of time as the screensaver.  Moving the mouse or tapping to keyboard is supposed to wake it up.

Nope....nothing happens with that, and it's not after idle periods that it does this, it's while I'm working with it :(

---

### Post by w4ett on 2007-06-17
Is this a pci or agp card?  Are you using the Xorg ATI driver or the Legacy driver?  I'm using a 9200 and had to mod xorg.conf a bit to get it running right.

---

### Post by Ronin_301 on 2007-06-17
Got it running a-okay, just a little surprised as to how. All I did was shut down the feature that automatically turns the monitor off after x minutes of inactivity (not the screen saver, but the actual monitor shutdown), and I haven't had a problem since. Interesting...

---

### Post by w4ett on 2007-06-17
> **Ronin_301 said:**
> Got it running a-okay, just a little surprised as to how. All I did was shut down the feature that automatically turns the monitor off after x minutes of inactivity (not the screen saver, but the actual monitor shutdown), and I haven't had a problem since. Interesting...

Gotta remember that one.  One more thing to add to the troubleshooting checklist :)

---

### Post by steveneddy on 2007-06-17
Strange, but interesting.

---

### Post by Ronin_301 on 2007-06-17
Eh...spoke to soon...just did it again :-P

---

### Post by w4ett on 2007-06-17
> **w4ett said:**
> Is this a pci or agp card?  Are you using the Xorg ATI driver or the Legacy driver?  I'm using a 9200 and had to mod xorg.conf a bit to get it running right.

OK we're back to the above questions....LOL

---

### Post by Ronin_301 on 2007-06-17
PCI, and whichever driver came pre-loaded on Ubuntu.

---

