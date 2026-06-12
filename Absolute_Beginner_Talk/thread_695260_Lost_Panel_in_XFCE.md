---
title: "Lost Panel in XFCE"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Harley_Mark on 2008-02-12
Hi all, I am a noobie. I am running the latest version of Ubuntu. I have installed the Xubuntu desktop and was running XFCE. I mistakenly hit Alt + Control + Delete and the "Panel" bar at the top of the screen went MIA. Does anyone know how to restore this. It is almost impossible to use this without the panel bar.

Thanks

---

### Post by spiderbatdad on 2008-02-12
Alt-F2  enter xfce4-panel

---

### Post by Harley_Mark on 2008-02-12
This brings up a terminal session. When I shut down the terminal the "Panel goes away.
BTW Thanks

---

### Post by spiderbatdad on 2008-02-12
This is what I found: The command is:

xfce4-panel

Try that.

If it reappears and then vanishes when you close the terminal, do it again but leave the terminal open. Then reboot, keeping the terminal open and ensuring that the "save session" box is checked.

From this post: [http://ubuntuforums.org/showthread.php?t=322159](http://ubuntuforums.org/showthread.php?t=322159)

---

### Post by psquared89 on 2008-07-14
You don't need to reboot. If you just open a shell and run the command, then the panel process is "owned" by that shell. When you kill a parent process (in this case the shell), all of its children (in this case the panel) are killed to.

What you need to do is type:

xfce4-panel &
disown %xfce4-panel

The & starts the panel as a background process (letting you type at the terminal still), and the disown command disowns the panel process from the terminal, so that when you close the terminal, you don't lose the panel.  (If you ever forget to start a command with &, you can also hit Ctrl-Z to STOP a running command, and then type "bg" to background the process, then disown the same way).

---

