---
title: "Auto-start programs?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Tomkin on 2007-10-03
Here's a quick question with (hopefully) just as quick of an answer.

I have a script that launches several programs that I usually execute when I login (yakuake, kopete, wicd-tray, and so on). Where do I place this script so that it executes automatically on login?

---

### Post by peabody on 2007-10-03
You should be able to put a line for it in the Session control panel under preferences.

---

### Post by Tomkin on 2007-10-03
Oh, I forgot to mention I'm using Kubuntu, which (unless I'm mistaken) has a different control panel. Sorry. I've put it in my sig to avoid future confusion.

---

### Post by peabody on 2007-10-03
can't help you there, been a long time since I used KDE.  I believe there are Kubuntu specific forums.

---

### Post by bsharp on 2007-10-03
Sorry to ask a question on someone else's thread, but how would you do this the "other way" meaning editing a file or whatever that is kinda like "autoexec.bat" in DOS?

---

### Post by Tomkin on 2007-10-03
Actually, that would be helpful for me to know as well - if I know which script to edit, I can just add them manually.

---

### Post by peabody on 2007-10-03
Specifically the OP was asking for how to run a program at launch, which you can do on regular Ubuntu using the Session control panel under preferences.  As for writing your own scripts, there's lots of ways to do that, bash, python, etc, etc.

---

### Post by bsharp on 2007-10-03
Writing the scripts isn't the problem, what I (we) would like to know is how to manually make them run on startup (and as powerful as the Linux CLI is, there *has* to be a way)

---

### Post by peabody on 2007-10-03
Startup of the actual machine?

couple of things you can do.

Make sure your script is executable and doesn't have a '.' in its filename and dump it in /etc/rc.boot.
Another way is to manually add the script contents to /etc/rc.local
Another way is to create a sysv init script to go in init.d and be managed by the sysv init tools.

---

### Post by Dr Small on 2007-10-03
> **bsharp said:**
> Writing the scripts isn't the problem, what I (we) would like to know is how to manually make them run on startup (and as powerful as the Linux CLI is, there *has* to be a way)
Maybe something like this ?:
```
ln -s /path/to/script /etc/init.d/script
update-rc.d script defaults
```

I used that method for starting LAMP at startup. Only, I have no idea how to remove it.
Perhaps someone else with more knowledge can explain that.

Dr Small

---

### Post by Tomkin on 2007-10-03
After some fiddling around (Autostart is in the About Me tab? You're kidding, right?) I learned that you can put links to apps is the ~/.kde/Autostart folder. I don't know if it works that way in Gnome, though. And I still have to reboot to test it. Joy!

---

### Post by peabody on 2007-10-03
> **Tomkin said:**
> After some fiddling around (Autostart is in the About Me tab? You're kidding, right?) I learned that you can put links to apps is the ~/.kde/Autostart folder. I don't know if it works that way in Gnome, though. And I still have to reboot to test it. Joy!

Logging out and logging in doesn't work?

---

