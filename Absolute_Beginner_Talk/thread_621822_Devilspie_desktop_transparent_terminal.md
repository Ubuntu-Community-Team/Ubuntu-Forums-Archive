---
title: "Devilspie desktop transparent terminal"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by petit.padavoine on 2007-11-24
I'm using devilspie to have a transparent terminal load in the top left corner of my desktop, with no borders, etc...
It looks fabulous, and I love it.
However, I have a small problem.
The terminal appears and everything works, but I have no way to switch to it except by minimizing all other windows. Alt Tab doesn't work, and clicking on the "show desktop" button hides the terminal...

This is my devilspie config file:
```

(if
(matches (window_name) "DesktopConsole")
#I have a special gnome-terminal profile called DesktopConsole, used only for the transparent #desktop terminal
(begin
(set_workspace 4)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
#I've considered removing this last line so that Alt Tab can switch to it, but then it appears in the #taskbar and I don't want that
(wintype "utility")
(geometry "+50+50")
(geometry "924×668")
)
)


```

Any help? How can I easily switch to it?

---

### Post by Forlong on 2007-11-24
You can access it via [Alt]+[Tab] when removing the (skip_tasklist) option - but then it will show up in the Window List.

There's no way I'm aware of to prevent a window from minimizing when using Show Desktop (without Compiz).

---

### Post by u-foka on 2008-01-28
Hy!

Maybe you can use superswitcher with your existing configuration, and then you can select your desktop terminal with [super]+[tab]

([http://code.google.com/p/superswitcher/](http://code.google.com/p/superswitcher/))

---

