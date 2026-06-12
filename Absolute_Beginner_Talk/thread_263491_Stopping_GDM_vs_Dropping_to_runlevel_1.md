---
title: "Stopping GDM vs Dropping to runlevel 1"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by chrisfay on 2006-09-23
I'm running a server that doesnt need a display any longer. I'm trying to figure out the best way to drop the display manager; I know I can just stop gdm but is that going to save system resources at all or should I drop to runlevel 1? 

What are the benefits of doing either?

---

### Post by Lakefall on 2006-09-23
> **chrisfay said:**
> I'm running a server that doesnt need a display any longer. I'm trying to figure out the best way to drop the display manager; I know I can just stop gdm but is that going to save system resources at all or should I drop to runlevel 1?
Dropping to runlevel 1 is a bad idea. It's the runlevel used to enter the single user mode, which is a mode intended for special system administration tasks, not for normal operation.

In case you do want to, I think the most correct way to enter the single user mode is to type "sudo shutdown now".

Simply stopping the gdm ("sudo /etc/init.d/gdm stop") should do what you want, but you can also completely uninstall it ("sudo apt-get remove gdm"). The latter will also uninstall ubuntu-desktop, which is a pretty useless package if you know what you are doing.

If you do uninstall gdm, you can still start X with the "startx" command. But if the server doesn't have a display, you can get rid of the X server too. You can still run graphical programs over a network as long as you have X on the machine you use to connect to the server.

---

