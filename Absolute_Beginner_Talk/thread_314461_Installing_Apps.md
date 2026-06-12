---
title: "Installing Apps"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Connie on 2006-12-07
Good Afternoon,  I'm a noob just converting my HP zt3300 lapton from Winduh!s to Dapper.  Install was successful; mounting fat32 drives completed; email established and all that other startup stuff completed.  My issue is this;  I used Synaptic to install clamav and fpm, but the apps don't appear on any dropdown menus or any 'taskbar'.  I've searched for 'fpm' and 'clamav' without results.  Yet Synaptic says they're installed.  Any guidance for this noob as to where to find the apps and how to launch them from a menu?  All help appreciated and Thanks in advance.

---

### Post by igknighted on 2006-12-07
if you open a terminal you can run them by typing (I believe) 'clamav' and 'fpm' respectively.  If you right click a file I believe you have a choice to scan with clamav as well, although I never use an av, so I'm not sure. Honestly, unless you're worried about passing viruses to windows people (or if you are running a mail server) I wouldn't worry about an av, its not needed.

You can create a custom launcher for them, using the same command as the terminal if you want.  I am not sure how alacarte works exactly, but to add it to the drop down menus you use that (assuming you are using gnome)

---

### Post by Connie on 2006-12-07
Thank you sir, I will try that later tonight when I get off work.  Connie

---

### Post by tonyr1988 on 2006-12-07
ClamAV is actually under System -> AntiVirus -> AntiVirus

I haven't used FPM before, but I just installed it, and it looks like it wasn't under any of the menus. However, you could run it from the Terminal (Applications -> Accessories -> Terminal) and type in 'fpm' (without quotes) and it should be running.

You could also right-click Applications, click Edit Menus, and add it yourself by doing this:

-In the left pane, click the category you want it to be under (System Tools, maybe?)
-File -> New Entry
-Name: FPM (or Password Manager, or whatever you want it to be)
-Comment: anything, or leave it blank. This is the text that'll show up when you put your mouse over the menu item
-Command: fpm
-Click the No Icon button. A window should show up.
-At the top, it'll say

> /usr/share/pixmaps/

change it to

> /usr/share/pixmaps/fpm

and click logo.xpm

-OK, OK, Close

Tada! It should work. You may have to open the Terminal again (Applications -> Accessories -> Terminal) and type:

> sudo killall gnome-panels

Hope it works

PS This is all assuming you're using Gnome (Ubuntu) and not KDE (Kubuntu) or XFCE (Xubuntu) or anything else. I have no clue about the other DEs.

---

### Post by Connie on 2006-12-07
Again my thanks to you and the other person that offered their help. Connie

---

### Post by drphilngood on 2006-12-07
Actually you need to install ClamTk to have a GUI front-end for ClamAV.  Just see here:

[Clamtk]("http://clamtk.sourceforge.net/")

You can install it by entering the following in a terminal:

```
sudo apt-get install clamtk
```

You can then run it by entering ¨clamtk¨ in a terminal or ¨sudo clamtk¨ when you want to update your definitions and/or scan files with root-only access.

Hope this helps.

---

