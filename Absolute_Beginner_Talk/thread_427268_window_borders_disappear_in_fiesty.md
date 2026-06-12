---
title: "window borders disappear in fiesty"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2007-04-29
Had this happen yesterday but it was a fresh install and i hit enable 3d effects.  

I re installed and this time DIDNT  touch anything .   On a restart , the window borders and minimized windows names are gone ,

in gnome failsafe all is well . so its a start up script causing the problem ( me thinks ) 

any one else have this problem ??

Stephen

---

### Post by juantovarm on 2007-04-29
might be a silly question, but have do you have the emmerald theme manager installed?

you might want to visit

 [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

---

### Post by basilwatson on 2007-04-29
> **juantovarm said:**
> might be a silly question, but have do you have the emmerald theme manager installed?

you might want to visit

 [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

No I dont think so its a straight fiesty install .  I am not sure if that is part of the package ..but no i havent added any effects 

I did ,,, lost the borders , thought it was beryl , so did a fresh install ,,( its quicker ) 

Stephen

---

### Post by juantovarm on 2007-04-29
The icon is a green emmerald, the thing is that you might have the acceleration, but without the themes, you won't get the borders or anything, visit that page

---

### Post by kvonb on 2007-04-29
Did you install the restricted driver for your video card?

For GLdesktop you need a 3d capable card which is supported, ie an Intel 9xx, ATI, or Nvidia card.

First you have to enable the restricted driver from the system menu, then you can enable the 3d desktop effects.

You can't just enable 3d effects on the default video driver.

---

### Post by 3rdalbum on 2007-04-29
Boot up, and then go into the terminal. Type "metacity" and hit Enter. If you don't get the window borders come back, then please take note of if there are any error messages, and post them here.

If the borders come back, you should put that command into the Startup Applications (System > Preferences > Session).

---

### Post by basilwatson on 2007-04-29
> **3rdalbum said:**
> Boot up, and then go into the terminal. Type "metacity" and hit Enter. If you don't get the window borders come back, then please take note of if there are any error messages, and post them here.

If the borders come back, you should put that command into the Startup Applications (System > Preferences > Session).

ok typing metacity has them back up ,,  but it was a fresh install ...  ..  so I really dont understand 

anyway as I type this its rebooting  we wiill see!!!!:lolflag: 

ok thats good its working ,,, Thanks for the input folks ONE&#12288;day Ill be able o return the favor !!!!

Stephen

---

### Post by Rhune on 2007-04-29
> **3rdalbum said:**
> Boot up, and then go into the terminal. Type "metacity" and hit Enter. If you don't get the window borders come back, then please take note of if there are any error messages, and post them here.

If the borders come back, you should put that command into the Startup Applications (System > Preferences > Session).

Adding Metacity as a startup app isn't a good solution if you are using saved sessions since it will start all your apps in the first workspace and forget all about your previous session settings when Metacity is restarted.

The cause of the Metacity problem seems to be a bug when saving the session upon logout while still running session-unaware apps like Firefox. Killing Firefox before logging out or disabling the "Save sessions automatically" option fixes the problem.

See the following threads for more info:
[http://ubuntuforums.org/showthread.php?t=419523&page=2](http://ubuntuforums.org/showthread.php?t=419523&page=2)
[http://ubuntuforums.org/showthread.php?t=406693&highlight=metacity+no+borders](http://ubuntuforums.org/showthread.php?t=406693&highlight=metacity+no+borders)

---

