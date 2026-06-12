---
title: "Install Steam And CSS on Ubuntu"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Kainoi on 2007-12-07
How do i get steam to install?

Being and .msi file wine doesnt know how to execute it,

also how can i install css also?

Thanks,

Noob

Links to guides or direct guides apprietciated.

---

### Post by PeterJS on 2007-12-07
Here's a guide it's a bit outdated, step 3 is no longer needed:
[http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)

I've had a wine developer personally scold me for this one, but if you've got a dual boot system you can symlink your windows steam install in to your wine folder. It's a bit more difficult to set up as steam doesn't handle having the entire folder symlinked well, but you can stitch together a patch work of copies and symlinks to massively conserve space.

---

### Post by daimaru on 2007-12-07
just execute the .msi file from terminal using :
```
wine steam.msi
```
installing counterstrike source should be as easy as clicking install in steam... 
if your using ati card though you can stop right here, because your steam games including css will only lag. if you have nvidia go ahead everything should be fine.

---

### Post by Nehallyn on 2007-12-07
You need to put the SteamInstall.msi into c:\\ and then run
```
wine msiexec /i c:\\SteamInstall.msi
```
from any terminal. Please note you will need the Tahoma TTF to run Steam, [you can get it here]("http://www.ocf.berkeley.edu/~gordeon/tahoma.zip").

You can install CounterStrike from the CD, but it needs extra stuff is what I understand. I just set the game to download the hard way, it should be done when I wake up later today.

I hope all this is acurate, I just started installation of Wine and Steam a few minutes ago. Actually, I just installed Ubuntu 7.10 today, so this is my first day with the new OS.

---

### Post by Kainoi on 2007-12-07
Cant get any of this to work...

Every time install it it installs fine but then it says you can have more than one copy of steam running at same time.

Also it says in wine terminal
~$ Xlib:  extension "XFree86-DRI" missing on display ":1.0".

I look that up in synaptic manager and i get nothing

Help me please,

Ubuntu is so confusing i almost want to go back to vista

---

### Post by Kainoi on 2007-12-07
Oh yeah im using ubuntu 7.10

---

### Post by PeterJS on 2007-12-07
> **Kainoi said:**
> 
Also it says in wine terminal
~$ Xlib:  extension "XFree86-DRI" missing on display ":1.0".


DRI is the Direct Render Interface, and is an element of graphics driver. So this raises the question what graphics card do you have and what drivers are you using?

---

### Post by zorkerz on 2007-12-22
Hey im trying to install steam to a different than default directory outside of wine's c:\ drive. I am not sure how to tell steam to do this.

---

