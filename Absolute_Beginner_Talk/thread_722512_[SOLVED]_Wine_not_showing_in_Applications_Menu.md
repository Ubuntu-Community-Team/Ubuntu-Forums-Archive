---
title: "[SOLVED] Wine not showing in Applications Menu"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by takuhii on 2008-03-12
I've just installed the latest version of Wine from the repos and it hasn't appeared in my Applications Menu, There used to be a Wine option with the old versions, this is the first time I have installed it since upgrading to Gutsy

---

### Post by forrestcupp on 2008-03-12
Restart your computer and it should be there.  You may be able to just do a ctrl-alt-backspace.

---

### Post by gi2k15 on 2008-03-12
The same is happening to me, but after I reinstalled WIne. I unistalled it using the Add/Remove programs, removed the .wine folder then installed it again. The menu was not showing anymore (it was on the 1st installation). I restarted the X and then the PC, didn't work as well. Tried to edit the Applications menu to see if the Wine menu was listed there, but it wasn't.

---

### Post by forrestcupp on 2008-03-12
Try opening a terminal and running
```
winecfg
```
Then restart and see if it's there.

---

### Post by gi2k15 on 2008-03-12
Did it, didn't work.

---

### Post by takuhii on 2008-03-12
didn't work for me either :( According to WineHQ, this seems to be happening alot to Ubuntu Users, maybe a Distro issue...

---

### Post by ajgreeny on 2008-03-12
Are you using the wine version from the ubuntu repos or direct from the wine hq repos.  I seem to remember reading that the wine's own repos version has this glitch.  I installed the ubuntu repos ve4rsion and updated to the newest version from wine direct and the menu item still is there and works.  I don't know if that is always so, but it could be worth a try or you can always make your own launcher using alacarte and add it.  I don't know if it will then pick up all the applications you install, but it's something to try.

---

### Post by Oldsoldier2003 on 2008-03-12
> **ajgreeny said:**
> Are you using the wine version from the ubuntu repos or direct from the wine hq repos.  I seem to remember reading that the wine's own repos version has this glitch.  I installed the ubuntu repos ve4rsion and updated to the newest version from wine direct and the menu item still is there and works.  I don't know if that is always so, but it could be worth a try or you can always make your own launcher using alacarte and add it.  I don't know if it will then pick up all the applications you install, but it's something to try.

Every time i have attempted to use a newer version of wine than what is in the Ubuntu repo i've had more problems than were acceptable. Ive always ended up reverting to the repo version. Also using wine-doors has always created more issues than it was worth to me. My advice would be to purge wine and go back to the stable repo version.

---

### Post by ajgreeny on 2008-03-12
I've had no problems with wine direct from wine hq, but I have to admit I seldom need to use it and it tends to be only for reading lotus smartsuite files from an old windows folder.  I'm not a gamer so have no other real interest in it, though I have also tried the windows version of Mailwasher Free, which works well,  but so does pop3browser, so I use that as it's quicker by far.

---

### Post by gi2k15 on 2008-03-12
I'm using the Ubuntu version of the file, gonna try to download the WineHQ version to see if it'll work.

EDIT: didn't need to do it. I removed the ~/.config/menus folder and worked, everything is normal now. You can try it and see if it works, but do a backup of the folder just in case.

---

### Post by takuhii on 2008-03-13
cheers for all the help guys, I'll give this a whirl tonight, when I get home from work...

I even tried manually firing up WINECFG and that didn't help :(

---

