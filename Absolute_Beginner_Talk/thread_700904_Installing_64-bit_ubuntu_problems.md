---
title: "Installing 64-bit ubuntu problems"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Dragabain on 2008-02-18
Hey guys,

I installed ubuntu on my laptop and had practically no issues so I figured the same would hold true for installing it on my Desktop.  I went with 64-bit ubuntu as I have 4GB of memory and hope to put anther 4GB in there soon.  The problem I'm facing is the splash screen doesn't pop up, and the light on my monitor just blinks.  I know the computer works fine as gentoo worked fine on it.  Here are my system specs:

Q6600
P35 Chipset
4GB of memory
Nvidia 8800GTX
RT61 card

Any help would be greatly appreciated.

---

### Post by JoshuaRL on 2008-02-18
What driver are you using?  I would suggest using the vesa one on your video card until you can download and run Envy.  Your problem sounds like that type of issue.

---

### Post by Dragabain on 2008-02-19
Well, fto be honest I don't know what driver I'm using.  The only way I can use the system at the moment is to start it up in safe mode and use the vesa drive and manually start GDM.  Regaurdless of what driver I put to use in my Xorg.conf the system doesn't display anything after grub when attempting to boot normally.

---

### Post by Hobo Joe on 2008-02-19
I've just figured out a simliar problem on mine computer, with a similar GPU (8800GTS).

What you need to do is boot into recovery mode, then type this:
```

sudo nano -w /boot/grub/menu.lst

```
Scroll down till you get to a section that looks like this:
> title Ubuntu, kernel 2.6.12-9-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot
And change the 'splash' to 'nosplash'. Leave everything else as is.
Ctrl+O to save, Ctrl+X to exit, then reboot.

When editing this file be VERY CAREFUL. Messing it up would force you to reinstall GRUB which would take some time.

I still have no idea what causes the problem, or why this fixes it, but it does, so I'm not complaining! :)

---

### Post by Dragabain on 2008-02-19
That works like a charm thanks!  You think its because I'm using such a high resolution on the monitor? (1920x1200)

---

### Post by Hobo Joe on 2008-02-19
I don't think so, I was using it on a 1152x864 before, and now I'm on 1680x1050, had the same problem on both.

Glad it worked!

---

