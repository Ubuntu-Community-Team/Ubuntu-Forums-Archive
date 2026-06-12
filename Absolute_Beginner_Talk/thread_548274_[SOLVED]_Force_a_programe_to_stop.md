---
title: "[SOLVED] Force a programe to stop"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Yizi on 2007-09-11
How you can force a program to close, i curently run program and it's stock how can i stop it. in Windows you have a option from task manager.

---

### Post by BrendanM on 2007-09-11
if you go to system->administration->system monitor, you'll see something similar to the windows task manager. Note that it's better to try Ending proceesses rather than Killing them. Only kill if you have to.

You can set up the system monitor to pop up with hotkeys, if you want. (I set mine to ctrl+alt+del ... old habits die hard)

Edit: Go to System-> Preferences->Keyboard Shortcuts to configure your hotkeys.

---

### Post by RomeReactor on 2007-09-11
Hi. You can also press ALT+F2, type **xkill**, and your cursor will turn into a skull and crossbones; any application you **left-click** on will close, and your cursor will return to normal. If you decide not to close the application after all, or it closed by itself, **right-click** anywhere to return your cursor to normal.

---

### Post by Yizi on 2007-09-11
> **RomeReactor said:**
> Hi. You can also press ALT+F2, type **xkill**, and your cursor will turn into a skull and crossbones; any application you **left-click** on will close, and your cursor will return to normal. If you decide not to close the application after all, or it closed by itself, **right-click** anywhere to return your cursor to normal.

Wow this one is so evil :evil:

---

### Post by cyrustajik on 2008-01-06
wow,
its well evil
i like it :D

cheers lads

---

### Post by kudos1uk on 2008-01-06
:(
Wish I had the skull and crossbones, xubuntu only an "x"

---

### Post by Majorix on 2008-01-06
You can also type
```
killall *appname*
```
But then you have to know the name of the running process. I don't know if an asterisk(*) would work.

---

### Post by MarilenCorciovei on 2008-01-08
You can also do a pkill program name if you don't know the actual name. pkill firefox will work because the name is firefox-bin

---

