---
title: "How do display boot details in kubuntu?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Kamu on 2007-03-18
I recently upgraded my kubuntu laptop from dapper to edgy and am quite happy with the improvements.  One thing bothers me though.

In dapper, during boot, I could see the boot details (processes and interfaces being initialized, etc).  In edgy, those details are hidden and I only see the kubuntu splash image and a progress bar.  That bar gets stuck for a while about half way through before what is I suspect something timing out.  I would like to be able to see what takes so long so I would like to restore the dapper behavior for the boot screen... I've looked around but no luck finding the information.  Anyone knows?

---

### Post by meborc on 2007-03-18
in grub, press "e" before choosing the kernel... then edit the boot line and delete the "quiet" option (don't worry, the damage is not permanent)

this will give you the text boot, not the splash one... and you should be able to see where the hang is... i don't think there is a way to display the boot sequence like in dapper though :(

---

### Post by NikoC on 2007-03-18
You could do:

sudo gedit /boot/grub/menu.lst

Find the line of the kernel you are booting

e.g.:  kernel /boot/vmlinuz-2.6.20-11-386 root=UUID=ddb93e65-d673-4f80-bc23-ff20344dac7c ro quiet splash

Remove the 'quiet', save and you'll get a splash screen with below it the booting process.
For complete verbose mode just remove 'quiet' and 'splash' and replace with the word 'verbose'.
To boot in a higher resolution you could also add 'vga=number' where number equals for example '792' which gives you a resolution of 1024x768. You could google for some other figures.

---

### Post by meborc on 2007-03-18
> **NikoC said:**
> You could do:

sudo gedit /boot/grub/menu.lst

Find the line of the kernel you are booting

e.g.:  kernel /boot/vmlinuz-2.6.20-11-386 root=UUID=ddb93e65-d673-4f80-bc23-ff20344dac7c ro quiet splash

Remove the 'quiet', save and you'll get a splash screen with below it the booting process.
For complete verbose mode just remove 'quiet' and 'splash' and replace with the word 'verbose'.
To boot in a higher resolution you could also add 'vga=number' where number equals for example '792' which gives you a resolution of 1024x768. You could google for some other figures.

this will work also, but this is a permanent fix (so you will have to change everything back later)

---

### Post by Kamu on 2007-03-18
Indeed, NikoC's solution works perfectly.  I prefer actually to have the behavior set like that permanently, thanks a lot to you both!

---

### Post by kwilliam on 2007-04-05
Is there a way to get the "pretty" verboseness of Dapper back?  I really miss it. :-(  Is there an alternative usplash (or whatever its called) theme?

---

