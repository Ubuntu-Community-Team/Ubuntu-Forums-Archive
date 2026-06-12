---
title: "Ctrl+Alt+Delete in Compiz Fusion"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2007-10-19
In Ubuntu 7.04 with Metacity I had a shortcut key for Ctrl+Alt+Delete that opened the Gnome system monitor like in Windows.

I used these two codes to change it.

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

Now I got Ubuntu 7.10 with Compiz Fusion instead of Metacity. How do I change my shortcut to behave like in Metacity? :)

---

### Post by Wikzo on 2007-10-19
.

---

### Post by Gio-van-I on 2007-10-19
I also have a shortcut I usually use. Normally I set alt + F3 for opening a terminal. I did this through keyboard shortcuts.
When I did this in Gutsy and tried to use alt + F3 I got the deskbar applet...
Guessing compiz overrules keyboard shortcuts.

How do you edit compiz safely?

---

### Post by Wikzo on 2007-10-20
Bump.

---

### Post by Wikzo on 2007-10-24
BUMP again.

---

### Post by realvz on 2007-10-24
metacity shortcuts should still work with compiz fusion...is it not working now?

---

### Post by Wikzo on 2007-10-24
No, they don't (as I wrote in my first post) :)

---

### Post by akiratheoni on 2007-10-24
I'm not 100% sure about this because I'm at school right now and not on Ubuntu, but isn't there an option under the General Options in the Compiz-Fusion settings manager that allows you to set shortcut commands?

---

### Post by Wikzo on 2007-10-24
Tried serching, but can't find anything there :\

---

### Post by robzon on 2007-10-26
Install CompizConfig Settings Manager from the repos, it will show up in System/Preferences. Run it, go to "General Options" and define your commands in "Commands" tab and then assign them shorcuts in "Actions" tab.
It's there for sure :)

---

