---
title: "xfce problem"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by moon_dog on 2006-03-30
i accidentally removed ubuntu-desktop when i removed openoffice.  i reinstalled it, and ever since then my XFCE desktop is screwed.  all it gives me is a blank screen and the mouse pointer.  right now i'm using GNOME.  i tried removing and reinstalling XFCE, but nothing seems to work.  these are the commands i used
```
sudo apt-get remove xubuntu-desktop
```
```
sudo apt-get install xubuntu-desktop wdm
```

my last resort is to reinstall everything but i don't really want to do that because it took forever to install the driver for my video card.

---

### Post by johnnymac on 2006-03-30
Try this....

Use synaptic and find the xfce desktop stuff.  Select it for removal, but make sure you select COMPLETE REMOVAL.  This should get all the residual crap from tmp and such.  Once that's done, re-install the xfce crud.  I suggest this 'cause I had a similar problem and the simple apt-get remove didn't do it for me.

Good luck

---

### Post by moon_dog on 2006-03-30
still no go, all i get is a blank screen with the mouse.  right click doesn't work at all.

---

### Post by JShadow on 2006-03-31
Can you log into XFCE as a different user than the one you normally use? Maybe some configuration in your home directory is causing a problem.

---

### Post by taurus on 2006-03-31
Try removing ~/.config from a terminal and see if you can log into Xfce4!!!
```

rm -rf ~/.config

```

---

### Post by trent dillman on 2006-03-31
Also, look in /tmp in different folders that contain your user name and look for and delete any lock files.

```
find /tmp -name lock
```

---

