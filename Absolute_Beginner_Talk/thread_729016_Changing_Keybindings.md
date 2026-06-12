---
title: "Changing Keybindings"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by tprzepiorka on 2008-03-19
Hello,
I just installed Gnome-Do application launcher, but I want to change it so that instead of launching by pressing Windows+Space it launches when I press Alt+Space. I went into gconf-editor and set the Value of "key_binding" to "<Alt>space". I closed, but when I try to launch using Alt and Space nothing happens. Also I might note that under "Key Documentation" it says "This Key has no schema". I have tried editing under gconf-editor using sudo and just launching it without sudo.
Thanks in advanced.

---

### Post by BluntBox on 2008-03-19
If you run gnome-do from the terminal does it say the "Binding '<Alt>space' failed!"?

It did this to me when I bound it to a key combination that was in already set in System -> Preferences -> Keyboard Shortcuts.

Once I disabled Alt+Space from there and restarted Gnome-do it worked fine.

---

### Post by tprzepiorka on 2008-03-22
Nope, when I run Gnome-Do I get no messages or anything. If I run with Sudo then it says many things, but not that the binding failed. If I change the binding then i get
```
3/22/2008 4:14:02 PM [Info]: Binding key 'Alt+Space' for '/apps/gnome-do/preferences/key_binding'. You may change this keybinding with Configuration Editor (gconf-editor).
```
However there was a conflicting entry in the keyboard shortcuts, but I fixed that and it still doesn't work. I'm not sure I am entering in the entry correct (is it Alt+Space, <Alt>+Space, etc.).
Thanks for the reply.

---

