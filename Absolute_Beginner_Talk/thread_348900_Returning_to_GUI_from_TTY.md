---
title: "Returning to GUI from TTY"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-01-29
After exiting Gnome (GUI) to use TTY, how do I return to Gnome?

I've tried **logout** and **exit**, but they just leave me stuck at the TTY username/password loop.  Typing **reboot** obviously reboots the system which isn't at all what I want to do.

My original Gnome (or for that matter, KDE) session evidently remains active because in TTY mode I can use the network connection I established in the GUI.  But I can't figure out how to return from TTY mode to that evidently still extant Gnome session.

Cheers & thanks,
Ric
SFO

---

### Post by mcglnx on 2007-01-29
What do you mean by 'exiting Gnome'?
Normally the X prompt should pop up again.

Otherwise, try Ctrl+Alt+F7 to go to X, Ctr+Alt+F1 for console.

Try to see errors as well in /var/log/Xorg.0.log

HTH,
D

---

### Post by Phrawm48 on 2007-01-29
Ah, ok!  In TTY (a.k.a. console mode) CTRL+ALT+F7 pops me back into the GUI.  That works great and answers my question.

My confusion stemmed from my use of Gnome's **Log Out** command to get another GUI dialog box, from which I then selected **Console**.  I thought I needed to similarly log out of the console session or otherwise perform a CLI command to get back to Gnome.

Now I understand that I don't...

Cheers & thanks for you help,
Ric
SFO

---

### Post by mcglnx on 2007-01-29
Welcome!
And enjoy this wonderfull world of Linux (resp Ubuntu)

---

### Post by glabouni on 2007-01-29
> < Virtual terminals >

Ctrl + Alt + F1
Switch to the first virtual terminal. In Linux, you can have several virtual terminals at the same time. The default is 6.

Ctrl + Alt + Fn
Switch to the nth virtual terminal. Because the number of virtual terminals is 6 by default, n = 1...6.

tty
Typing the tty command tells you what virtual terminal you're currently working in.

Ctrl + Alt + F7
Switch to the GUI. If you have X Window System running, it runs in the seventh virtual terminal by default. If X isn't running, this terminal is empty.
more on linux shortcuts on [http://www.tuxfiles.org/linuxhelp/shortcuts.html](http://www.tuxfiles.org/linuxhelp/shortcuts.html)

---

