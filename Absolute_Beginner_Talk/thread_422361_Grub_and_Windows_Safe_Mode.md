---
title: "Grub and Windows Safe Mode"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Ryokukitsune on 2007-04-25
well i have a bit of a problem with windows and it seems that the only solution is to run some software in safe mode however I installed grub as my boot loader and I dont know how to edit the menu.lst file so I cant set it up to boot to safe mode, if i even can. (i know to nano the file i just dont know what to put or where...)

does anyone know if there is some referecne to this?

any help aprchated **

---

### Post by Compyx on 2007-04-25
Aren't you supposed to mash F8 or something after having selected to boot Windows, so you can choose safe mode?

---

### Post by Patrick K on 2007-04-25
In W98 (I don't know anything about XP) I set up the Win boot menu (the one with safe mode among other options) to load and gave it a 10 second delay. So now after selecting Windows in Grub the Win boot menu comes up. If XP has a similar boot menu (which, in the case of W98, automatically comes up on a bad shutdown), perhaps you can do that.

---

### Post by Sef on 2007-04-25
> Aren't you supposed to mash F8 or something after having selected to boot Windows, so you can choose safe mode?

Yes, F8 boots you into safe mode.

---

### Post by aberry5555 on 2007-04-25
if you can still run windows, go to start, then run and type in "msconfig" this will bring up a window, select the "boot.ini" tab and tick "safe mode". now restart and it should work fine.

<--EDIT-->

Also, I know this is going to sound rude, but if you want a working windows I would stop using 98 :S

---

### Post by Ryokukitsune on 2007-04-26
well i was hoping to add a safemode entry to the menu.lst file i just dont know what to write, fiddeling with a boot loader has always made me lerry.

though the mashing of the f8 key did send it into safe mode its a bit of a task to catch it in time. my compute is pretty fast and if i dont catch it just as it loads i usualy have to restart and try again doing it threw windows [msconfig] means i have to toggel the settings after every use.

---

