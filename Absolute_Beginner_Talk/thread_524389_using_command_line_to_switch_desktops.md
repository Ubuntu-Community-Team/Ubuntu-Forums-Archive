---
title: "using command line to switch desktops"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Canuckelhead on 2007-08-13
Hello... thinking of a project and I'm wondering if there is a way to move back and forth between desktops in gnome using the command line rather than using the mouse?  

Thanks in advance!

---

### Post by proalan on 2007-08-13
The global shortcut keys are

CTRL + ALT + cursor left or right

I'm not aware of any command line way of doing it. Would the same terminal appear in each of the desktops?

---

### Post by RomeReactor on 2007-08-13
Hi. I'm not sure about the command line, but you can switch desktops by pressing CTRL+ALT and the LEFT or RIGHT arrows.

EDIT: **proalan** beat me to it.

---

### Post by jordanmthomas on 2007-08-13
It appears as though there's not.  I looked around and the best thing I could find is a command to tell you which desktop you are currently on:
```
xprop -root | grep '_NET_CURRENT_DESKTOP(CARDINAL)' | cut -f2 -d=
```
It will return 0 for desktop 1, 1 for desktop 2, and so on.

So, if you ever find out a way to switch, you can at least tell where you are first in case the way to switch is something to the effect of "go this many workspaces forward" or something.  [-(

---

### Post by Canuckelhead on 2007-08-13
hmmm  that helps somewhat...long term that will help out alot Jordan...  However,  I guess what I'm really looking for is a script I could creat that could be used to switch desktops quickly...  It is meant to be called from python...  I'm sure there must be a way but it is clearly more difficult than I had thought... thanks guys

---

### Post by olejorgen on 2007-08-13
Ugly, but if you can find a way to programaticallly send keystrokes, you'd be set

---

### Post by jordanmthomas on 2007-08-13
[http://www.penguin-soft.com/penguin/man/1/xte.html](http://www.penguin-soft.com/penguin/man/1/xte.html)

I'm not at a Linux box right now so I can't verify that this is what I think it is, but it appears that you can send keystrokes with this program.  Like olejorgen said, it's a bit hackish to do it like this but it could give you a start so you can work on the rest of your project until you find a more elegant solution.

---

### Post by Canuckelhead on 2007-08-14
That looks perfect for now!  Thanks guys.

---

