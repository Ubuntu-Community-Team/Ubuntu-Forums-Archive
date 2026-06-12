---
title: "[SOLVED] No text during boot, black screen only"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Arthur Archnix on 2007-12-16
I've removed usplash because I find all the video mode switches between power on and gdm to make to look a little amateurish. I'd rather just have text boot until gdm; 

text mode->gdm Rather than ->textmode->progressbar->textmode->gdm

In Feisty I just removed usplash then set a nice vga setting in menu.lst, however, I'm unable to replicate that in Gutsy.

I've removed quiet, splash from the end of my kernel line, tried vga=773, 791 and others. No matter what, it just shows a black screen until gdm. 

The only exception is if I pass an invalid vga option. When I do that I'm allowed to choose a new on or just press space to continue. If I press space to continue I see the progress, text mode booting is back. But the only way I've been able to see text mode while booting is by passing an invalid video number. 

Very confusing.

---

### Post by Kingsley on 2007-12-16
You should have only removed quiet.

---

### Post by Existentialist on 2007-12-16
To remove the splash screen and get text during booting I edited menu.lst:
>sudo nano /boot/grub/menu.lst

and changed the ubuntu option from something like this:

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro **quiet splash**
initrd /boot/initrd.img-2.6.17-10-generic
**quiet**
savedefault
boot

remove the stuff in bold to get something similar to:

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro
initrd /boot/initrd.img-2.6.17-10-generic
savedefault
boot

Save and reboot.  There should no longer be splash screens during boot or shutdown.

---

### Post by Arthur Archnix on 2007-12-18
ok... but if I don't uninstall usplash I have no problem making it go to text boot only. If I uninstall usplash then I can't get text unless I pass an undefined video number. This looks like a bug.

---

### Post by Arthur Archnix on 2008-01-09
I ended up just doing a clean install. Looking back, it's likely not a bug, I made so many changes and such over the preceding few weeks/months that I probably just messed something up.

---

