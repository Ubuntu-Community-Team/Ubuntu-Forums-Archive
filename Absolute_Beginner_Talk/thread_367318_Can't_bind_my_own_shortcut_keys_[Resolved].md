---
title: "Can't bind my own shortcut keys [Resolved]"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by CaptSaltyJack on 2007-02-22
I go to Prefs, Keyboard Shortcuts.. and I try to bind something for "Logout".. Ctrl-Alt-Del, didn't work.  I hit that combo and nothing happens.  In Kubuntu, that key sequence prompts you to log out/reboot/shutdown/etc, which is handy.  It doesn't need to be Ctrl-Alt-Del, but some shortcut key would be nice to have.  Why is this not working?

---

### Post by aysiu on 2007-02-22
Can you bind any of the other commands (besides Logout)?

Can you bind other key combinations?

---

### Post by kelbizzle on 2007-02-22
There ya go mate.
[http://ubuntuforums.org/showthread.php?t=308173&highlight=alt+del](http://ubuntuforums.org/showthread.php?t=308173&highlight=alt+del)

---

### Post by CaptSaltyJack on 2007-02-22
Oh thanks!  I'll probably report it as a bug though.. because really it should work in the Keyboard Shortcuts pref.  Shouldn't have to use gconf.

---

### Post by kelbizzle on 2007-02-22
your welcome. Right on...because a bug insn't a bug until someone reports it.

---

### Post by CaptSaltyJack on 2007-02-22
Nevermind, it's because Metacity isn't my window manager.. Emerald (Beryl) is.

Just FYI, this does not work for Beryl users.  Beryl uses Emerald as the window manager, not Metacity, so you must open the Beryl options, and under "General", look around.. you'll see "Commands" and "Shortcuts".. it works very similarly to Metacity.  You will find run_command_0, run_command_1, etc..and you can bind keys to those.

---

### Post by theprocyon on 2007-03-28
> **CaptSaltyJack said:**
> Nevermind, it's because Metacity isn't my window manager.. Emerald (Beryl) is.

Just FYI, this does not work for Beryl users.  Beryl uses Emerald as the window manager, not Metacity, so you must open the Beryl options, and under "General", look around.. you'll see "Commands" and "Shortcuts".. it works very similarly to Metacity.  You will find run_command_0, run_command_1, etc..and you can bind keys to those.

these right here, helped alot!!! tks mate, it's not hard to get there, but i wasn't able too do soo
tks alot :)

---

