---
title: "xorg.conf not reading properly on bootup?"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Dmize on 2006-11-04
I've recently installed Beryl/Compiz/Emerald and everything went smooth, i figured out the issue with lagging in startup ( .  emerald --replace) and worked great. But unfortunately, today, restarting my PC led me to a error in the GUI as it could not be loaded. I did back up my conf file prior, but im stuck at a terminal type prompt and not sure what to do. Now this occurred with me before, i just formated and restarted all over again. I'm trying to change that process and figure it out. Anyone have any suggestions? It happens with i try to load up my system, i get a terminal prompt and a error saying X server could not be loaded properly, then it says hit OK to view the output. Thanks for reading, If anyone has a tip please leave it. Thanks! ](*,) 

Derek.

---

### Post by CatKiller on 2006-11-04
If it's not starting because you've fiddled with your xorg.conf, you can restore you backup with a ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``` assuming that your backup was called xorg.conf.backup. You may need to press **Ctrl-Alt-F2** and log in before that will work.

---

