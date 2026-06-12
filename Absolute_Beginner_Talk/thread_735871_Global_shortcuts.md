---
title: "Global shortcuts"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Superdarion on 2008-03-26
I use amarok (ubuntu 7.10, gnome) for music playback and I use the global shortcuts option. It used to work fine with dapper but now, since I installed 7.10 there is some application that has the global shortcut super+c assigned to "Center mouse pointer on screen" and I haven't been able to find it. The  keybinding options in the System\Preferences menu doesn't have it.

Recently I tried exaile just for the fun of it. I liked amarok better so I unistalled exaile (sudo apt-get remove exaile) and later I realized that exaile had some global shortcuts assigned which didn't go away when I removed it and they just so happen to be the ones that amarok uses (and that I used myself even before they were set by default in some amarok version).

So... I was wondering, is there anywhere I could see ALL the shortcuts on my system? Or maybe a way to just remove them (and assign them back in Amarok).

---

### Post by Oldsoldier2003 on 2008-03-26
> **Superdarion said:**
> I use amarok (ubuntu 7.10, gnome) for music playback and I use the global shortcuts option. It used to work fine with dapper but now, since I installed 7.10 there is some application that has the global shortcut super+c assigned to "Center mouse pointer on screen" and I haven't been able to find it. The  keybinding options in the System\Preferences menu doesn't have it.

Recently I tried exaile just for the fun of it. I liked amarok better so I unistalled exaile (sudo apt-get remove exaile) and later I realized that exaile had some global shortcuts assigned which didn't go away when I removed it and they just so happen to be the ones that amarok uses (and that I used myself even before they were set by default in some amarok version).

So... I was wondering, is there anywhere I could see ALL the shortcuts on my system? Or maybe a way to just remove them (and assign them back in Amarok).

System>Preferences > Keyboard Shortcuts

---

### Post by Superdarion on 2008-03-26
> **Oldsoldier2003 said:**
> System>Preferences > Keyboard Shortcuts

It isn't there. I already checked and there is no super+c shortcut there (or any of the ones amarok uses).

---

### Post by kevang on 2008-07-11
The shortcuts are defined by Compiz plugins and hidden somewhere.

Here's what you can do: Install the package compizconfig-settings-manager. Then you'll have Advanced Compiz Options (or similar) in your Preferences menu. There you painstakingly go through all of the active plugins' settings to find the keybindings you want to change.

This is very bad. Key bindings shouldn't be hidden like that. Anyone know where the relevant config file is?

---

### Post by Gatemaze on 2008-07-16
run in a terminal gconf-editor and then go to apps>metacity>global-keybindings

---

### Post by cj2003 on 2008-07-17
They are also mentioned in this article:
[Useful Shortcut Keys In Ubuntu]("http://ubuntu-news.net/modules/news/article.php?storyid=4840")

---

