---
title: "gnome panel crashing"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by anurag_gupta on 2007-02-24
hi i recently installed kubuntu-desktop package onto my ubuntu install .. since then gdm doesn't starts (i hv to do it manually) gnome-panel keeps crashing and only the plane dsktop is left with some icons ....  i even reinstalled ubuntu-dektop package .. it doesn't works...

---

### Post by carney1979 on 2007-02-25
> since then gdm doesn't startsFrom a tty or gnome-panel or konsole, type:

```
sudo dpkg-reconfigure gdm
```Select gdm as your default login manager. 

Reboot or whatever your experience level allows to get gdm started.

> gnome-panel keeps crashingAfter logging into Gnome if the gnome-panel has crashed, hit ctrl-alt-f1 and login to the tty.

Then type:

```
killall gnome-panel
```Logout of the tty. Hit ctrl-alt-f7. If the gnome-panel has not restarted, then clear any error messages, right-click on the desktop and select "Open Terminal". In the terminal, type:

```
gnome-panel &
```After gnome-panel starts, logout of Gnome normally. This should save your session.

When you log back into Gnome, all should be alright.

Once in awhile, Gnome will think the panel is already running so it gives the error and stops trying to load gnome-panel.

Hope this helps!

David

---

