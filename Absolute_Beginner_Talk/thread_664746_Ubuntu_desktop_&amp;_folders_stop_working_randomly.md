---
title: "Ubuntu desktop &amp; folders stop working randomly"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Rubruquis on 2008-01-11
Sometimes all of a sudden, the desktop and the folders stop working. I can see the icons in the desktop but I can't click on them because the left click and the right click do not work. Also when this happens, I can't access to folders (like Home, Computer, etc).
The applications and everything else work fine, it is just the desktop and the folders. It gets fixed when I restart the computer.

Do you know what is causing the problem?

---

### Post by Rubruquis on 2008-01-11
By the way, if it will be any help, I'm using compiz-fusion, ATI Radeon X1900 series graphic card, XGL&Gnome.

---

### Post by disturbed1 on 2008-01-11
Sounds like nautilus is crashing. A few things can cause this, if you have network shares (NFS, CIFS, SMB) that were mounted, then went off line, tons of activity in a directory (creating new files, deleting files, changing files), 2 different file managers opened at the same (Thunar + Nautilus) can cause these issues.

Instead of restarting the PC, there are 3 quicker ways to fix this. Open the system monitor (System -> Administration -> System Monitor) right click on nautilus and kill task, open a term and type killall nautilus, hit ctrl-alt-backspace (this will restart Xorg and kill any/all apps runnings).

---

### Post by Rubruquis on 2008-01-11
the command "killall nautilus" solves the problem perfectly. thank you very much.

---

