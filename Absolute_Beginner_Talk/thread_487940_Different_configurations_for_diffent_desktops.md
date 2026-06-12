---
title: "Different configurations for diffent desktops?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by lawentzel on 2007-06-29
I have managed to get Gnome, KDE, Xfce and even Fluxbox installed on my computer.  [(Here is where I figured it out.)]("http://ubuntuforums.org/showthread.php?t=486923")  Can I configure them all differently?  Meaning, can I remove desktops icons, change the menus, and all of that without effecting the other ones?

XFce has duplicated a couple of icons on it's desktop.  KDE and Gnome seem to show all of each other's stuff in the menus.  Finally Fluxbox...  well it shows absolutely nothing in it's menu.  The only way I knew to shut it down  was to do a Control + Alt + Backspace.  So I have a lot to learn with it.

Any help would be appreciated.  Thank you in advance.

---

### Post by lawentzel on 2007-06-29
Anyone?

---

### Post by RedSquirrel on 2007-06-30
> **lawentzel said:**
> I have managed to get Gnome, KDE, Xfce and even Fluxbox installed on my computer.  [(Here is where I figured it out.)]("http://ubuntuforums.org/showthread.php?t=486923")  Can I configure them all differently?  Meaning, can I remove desktops icons, change the menus, and all of that without effecting the other ones?

XFce has duplicated a couple of icons on it's desktop.  KDE and Gnome seem to show all of each other's stuff in the menus.  Finally Fluxbox...  well it shows absolutely nothing in it's menu.  The only way I knew to shut it down  was to do a Control + Alt + Backspace.  So I have a lot to learn with it.

Any help would be appreciated.  Thank you in advance.

To get a basic Fluxbox menu, open a terminal (in GNOME or Xfce or KDE) and run the following:

```
sudo update-menus
```The next time you login to Fluxbox, you'll have a menu.

All of the Fluxbox configuration files are in ~/.fluxbox. Fluxbox has its own menu file, so it will not affect your menus in GNOME, Xfce, and KDE. 

There is a lot of information on these forums about Fluxbox. Just do a search and you'll probably find most of what you need. If not, just ask. ;)

Check out the links in my signature as well.

Bear in mind that you can't have desktop icons in Fluxbox without some third-party tool such as idesk, fbdesk, rox, etc. (I don't like desktop icons so I don't use those tools.)

---

