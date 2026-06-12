---
title: "ipod nano with gtkpod failing."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by twiistedkaos on 2007-08-08
I purchased an iPOD nano today, put some music on it, all was fine. Plugged it in to charge, and then unplugged it, music disapeared. Which didn't bother me to much, I figured I had it mounted and it just erased it's settings when I pulled the cord out. Plugged it back in, ran gtkpod, and I am getting this error when trying to load my iPOD:

Code:

Error initialising iPod: Problem creating iPod directory or file: '/media/ipod-1/iPod_Control/iTunes'.

Any ideas / Suggestions?

Alright, well somehow it magically fixed that error, how it's this one:

Code:

Error initialising iPod: Problem creating iPod directory or file: '/media/ipod-1/iPod_Control/Artwork'

Please help :(

---

### Post by Al3xK3aton on 2007-08-08
You shouldn't be using an iPod anyway unless you legitimately purchased all your music.

---

### Post by twiistedkaos on 2007-08-08
First off, music has nothing to do with my problem, furthermore, it's not really any concern to you. I was asking for help with my errors, not a lecture on piracay because you assume I am.

---

### Post by vexorian on 2007-08-08
> **Al3xK3aton said:**
> You shouldn't be using an iPod anyway unless you legitimately purchased all your music.
That's a little senseless.

Don't ever just unplug a flash device (does not matter if it is windows or Linux) always make sure to tell the operating system you want to eject it, in gnome you find the ipod in the desktop and do a right click then "eject"

now that you basically corrupted the mount point, you'll have to do a reboot.

---

### Post by twiistedkaos on 2007-08-09
> **vexorian said:**
> That's a little senseless.

Don't ever just unplug a flash device (does not matter if it is windows or Linux) always make sure to tell the operating system you want to eject it, in gnome you find the ipod in the desktop and do a right click then "eject"

now that you basically corrupted the mount point, you'll have to do a reboot.

I know it was an honest mistake, It wasn't displaying "Do not unplug" message, so I assumed it was fine. So if I corrupted the mountpoint, how do I fix that? If you're talking about reset to manufactor settings, tried that already.

---

### Post by vexorian on 2007-08-09
Doesn't rebooting the computer fix your issues? If the ipod itself got problems or has "crashed" you might google for rebooting the ipod, it is a trick that depends on the model.

---

### Post by tgalati4 on 2007-08-09
How did you initialize your iPod?  Was it with a Mac or a Windows PC?

I have heard anectodal reports of suble changes to the new iPods that trip up the current Linux iPod libraries.  When you initialized your iPod, you probably got hit up for an internet download to update it with the latest firmware.  That probably changed the database slightly so that it will be difficult to integrate with Linux.

Of course you can install Rockbox and say goodbye to iTunes.

---

### Post by twiistedkaos on 2007-08-09
rebooting ipod doesn't work, I have a feeling it's a bad sector on my ipod. I only ever initiated it on linux, never used it on windows or mac.

---

### Post by vexorian on 2007-08-09
Actually, just insert your ipod and browse it as if it was a flash disk.

find this folder: iPod_Control

Try to remove it, chances are it is owned by root, so you might need to use alt+f2, 
```
gksu nautilus
```

to get nautilus with super user priviledges. and be able to remove that folder. Then unmount the ipod and try again.

---

### Post by tgalati4 on 2007-08-09
I was under the impression that you had to first "authorize" the device to a Windows or Mac to correctly set up the device, then you can use it with gtkpod.  Otherwise it shows up as a mass storage device and you can put stuff on it, but the proprietary Apple firmware won't play because it was never "authorized" in the first place.

---

