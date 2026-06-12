---
title: "New Problem"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Frunkis on 2007-12-17
After trying and trying to get Ubuntu to load, I finally get the load screen where I have the option to install, I've already run the disk check and when I to Start or Install Ubuntu, it goes through the loading screen and then finally pops up with this:

*Starting deferred execution scheduler atd   [OK]
*Starting periodic command scheduler crond  [OK]
*Checking battery state...                              [OK]
*Running local boot scripts (/etc/rc.local)       [OK]

Any clue as to what this is? I do in fact have an ATI Radeon X1300 Pro graphics card which I saw where apparently there is an issue with compatibility, could this be causing the problem? Has anyone else seen this? It will not load past this screen, it stops here and does not move past. Any suggestions?

---

### Post by PmDematagoda on 2007-12-17
It is indeed a problem with the VGA card or most accurately, the X-Server. When you reach this part press Ctrl+Alt+F1 to get to a terminal, then do:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
The command returns the X-Server configurations back to their defaults.

After that is done do:-

```
sudo startx
```

---

### Post by Severun on 2007-12-17
I have an ATI X1400 card and I just found this little tidbit tonight.  It's got all kinds of information on the potential problems you'll see when using the fglrx driver.

[http://www.thinkwiki.org/wiki/Problems_with_fglrx]("http://www.thinkwiki.org/wiki/Problems_with_fglrx")

---

### Post by Frunkis on 2007-12-23
Still having issues with the install, I put in the codes above, and it still won't install. Any new suggestions?

---

