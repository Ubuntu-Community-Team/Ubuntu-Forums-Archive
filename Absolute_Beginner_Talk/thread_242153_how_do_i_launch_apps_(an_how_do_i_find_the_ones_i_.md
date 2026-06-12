---
title: "how do i launch apps? (an how do i find the ones i have downloaded)"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by chester on 2006-08-23
I used automatix and and the package manager to grab some apps i wanted to try and now i can't find them? Package manager tells me i have already installed them, but they are nowhere to be found. And once i find them, how do i "turn them on"

thanks in advance

---

### Post by 505 on 2006-08-23
Most apps install themselves in the Applications menu. Click on this menu, point to the right category (or just search through all of them) and click the program.

If you can't find it, the program probably didn't put an icon there (although most programs do). You can open a terminal, just type the application's name and press enter. Problem is of course, you need to know the name of the executable. Most of the time it's the same as the program's name.

If you really can't find it, open Synaptic Package Manager, search for the program you want to launch, right-click and select Properties, and go to the tab Installed Files. Look for files installed in a 'bin' dir (e.g. /bin, or /usr/bin). That's the application's name. Type that in the terminal to launch it.

---

### Post by HanZo on 2006-08-23
a nice trick is to use the application launcher in the gnome panel (it's an icon with two gears). if you don't have it in the gnome panel you can add it by right clicking the panel and and selecting the add to panle option.
once you have the icon click it, a small box with a text field appears. start typing the name of the app, it will autocomplete with the names of the executables installed... so you don't need to know the exact name...

---

### Post by chester on 2006-08-23
thank, that was very helpful

---

