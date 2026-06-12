---
title: "Can't find programs"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-17
When i download something from synaptics, it doesn't show up in any of the menus under applications.  Where do they install to and how do i access them?  Note this only happens with some programs.

---

### Post by daimaru on 2007-11-17
yeah some programs dont show up in menu.
if you know the command for the program (console) go to system->pref->main menu 
there you can add new program entries.

---

### Post by Arthur Archnix on 2007-11-17
It really depends on what program you're trying to install. For example, it shouldn't make a difference if you install thunderbird through add/remove, synaptic, or the cli.

I've had it occur that something was installed and didn't show up. But after a reboot I found it where it ought to be.

You may have to look in your menu editor and add some things manually if they're installed but don't show up even after a reboot.

---

### Post by daimaru on 2007-11-17
> **Arthur Archnix said:**
> Before trying to fix your system, be sure you know where your towel is. It is useful for: (1) muffling screams of frustration. (2) covering up evidence of ineptitude. (3) crying into.
its also useful when hitchhiking the galaxy :)

---

### Post by CatKiller on 2007-11-17
Only graphical applications will show up in the menu. Command line programs won't.

Sometimes the menu needs to be refreshed before they'll appear - **killall gnome-panel** will do it.

Menu items aren't kept in one file. They are stored as individual .desktop files that are indexed together.

---

