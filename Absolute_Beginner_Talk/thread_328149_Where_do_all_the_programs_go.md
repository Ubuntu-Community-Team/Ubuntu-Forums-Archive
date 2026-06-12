---
title: "Where do all the programs go"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by ubdai on 2006-12-30
When I run the add /remove routine and pick what s/w to install, it doesn't seem to want to appear on the pulldown application menu bar.

Where do the shortcuts go?

tia
ubdai

---

### Post by taurus on 2006-12-30
It depends on what you've installed.  Sometimes, log out and back in again would update the Applications menu...

---

### Post by markba on 2006-12-30
This sometimes happens. After a restart of the windows manager (GDM), they usually appear. You can quickly restart the window manager by hitting Ctrl-Alt-Backspace.
I'm not sure if this is a bug in the window manager or the application it self (not likely).
A bug in the installation package is also another possibility: when you manually add a shorcut in /usr/share/applications, a restart of GDM is always needed. Check in /usr/share/applications if the shortcut is indeed created (but not shown).

---

### Post by shanepardue on 2006-12-30
usually the shortcut is just the name of the program, but to find where it went if it isn't in the applications menu, type "whereis <package name>" in the command line. insert the program you installed where "package name" is. If that's too confusing, let me know!

---

### Post by Jussi01 on 2006-12-30
Also sometimes the menu doesnt select it to be shown - you can go system -> preferences -> Menu layout and you might find it there

---

### Post by ubdai on 2006-12-30
Thanks guys. That seems to have solved it. At least I know a command to help me find the progs now.

ubdai:)

---

