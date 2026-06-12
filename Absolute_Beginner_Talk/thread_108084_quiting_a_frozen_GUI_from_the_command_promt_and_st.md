---
title: "quiting a frozen GUI from the command promt and starting it again"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2005-12-25
My Gnome GUI is frozen.

With ctrl-alt-F1 I can switch to the command prompt. What can I type in to close the gui program and start it again.

Is there a linux version of ctrl-alt-del and the task manager?

---

### Post by dueY on 2005-12-25
[QUOTE=stroopwafel]My Gnome GUI is frozen.

With ctrl-alt-F1 I can switch to the command prompt. What can I type in to close the gui program and start it again.

Is there a linux version of ctrl-alt-del and the task manager?[/QUOTE]

I think you can type

sudo /etc/initd/gdm stop

to stop GNOME.  Try that.

---

### Post by bscbrit on 2005-12-25
Try hitting ctl-alt-backspace.

---

### Post by stroopwafel on 2005-12-25
i'm in /etc/init.d

"sudo gdm stop" works

when I try to start again.  (sudo gdm) it says:
---
gdm already running. Aborting!
---

How long do I have to wait?
Are there other commands to stop the gdm?

---

### Post by stroopwafel on 2005-12-25
[QUOTE=bscbrit]Try hitting ctl-alt-backspace.[/QUOTE]

Wow Thanks! That worked!

Pretty dangerous though, this key combination isn't it?

---

### Post by bscbrit on 2005-12-25
No, its not dangerous.  It simply stops the X system, which requires you to log on again. (X is the display system, in very simple terms)

---

### Post by bscbrit on 2005-12-25
Other ways to see what is happening are:

GUI - but you couldn't do this - Applications -> System Tools -> System Monitor

or

CLI - 'top'.  Read 'man top' for more details

---

