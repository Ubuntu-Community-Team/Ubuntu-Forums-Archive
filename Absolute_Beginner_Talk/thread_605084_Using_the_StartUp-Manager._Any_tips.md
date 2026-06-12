---
title: "Using the StartUp-Manager. Any tips?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by DavidJE13 on 2007-11-06
I'm going for all the bells & whistles, so figured I'd take a look at StartUp-Manager to see if I can improve the look of my Grub loader

but I know how easy it is to mess up the graphics when changing resolutions and colour depths in linux, and I don't want to end up in a situation where the loader's broken so I can't even get into safe mode

So any tips for how to avoid messing it up? or advice on what to do if I do?

---

### Post by Hospadar on 2007-11-06
well, if you do mess it up, you can always re-install grub (try getting a cd from the grub website, I think it's possible as well with the ubuntu livecd, if a little less straightforeward).  Also you (I believe) you could just back up your entire /boot folder and plop it back into place if stuff gets screwed up.

And while it certainly wouldn't hurt, backing up your home folder (at least any important stuff) probably isn't necesary.  If grub gets messed up and you can't figure out how to fix it, you can always retrieve that sort of thing with a livecd.

---

### Post by philinux on 2007-11-06
Gutsy. Yep - backup xorg.conf cos it aint pretty if you mess it up.

---

### Post by DavidJE13 on 2007-11-07
ok, well I've got a backup of xorg.conf already but I'm not actually changing that file - it's the Grub loader I'm changing the resolution of ;)
The main thing I was wondering was how to get into a command-line interface if I broke Grub, but the live CD idea should work I think. I'll make a backup of my menu.lst file first
I don't have any real data on my Ubuntu partition (it's a clean install of 7.10 and my data is on a different hard drive)

thanks for the replies :)

---

