---
title: "os won't boot"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-07
I am trying to boot my Ubuntu 7.10 OS, but after I enter the username and password, the screen goes blank and stays that way.  Do you know of any causes or resolutions for this, please?

---

### Post by LowSky on 2008-01-07
is it  a fresh install? have you installed or removed any software?

---

### Post by jhvillegas2 on 2008-01-07
It is a fresh install, and I just installed JRE 6, Flash player, and Azureus.

---

### Post by phidia on 2008-01-07
Try to open a tty by doing Alt+Ctrl+F1 (all 3 keys together) you can try to start your desktop by typing sudo startx. Note the output and/or search or copy and paste it here.

Some early releases of gutsy had this problem too but I'm assuming you're using the final release. You can just try restarting x though by Alt+Ctrl+BACKSPACE and see if that gets you a desktop.

---

### Post by jhvillegas2 on 2008-01-07
*********************OUTPUT**************************

xauth:  creating new authority file /home/john/.serverauth.5600


Fatal server error:
Server is already active for display 0
             If this server is no longer running, remove /tmp/.XO-lock and start again.

---

### Post by jhvillegas2 on 2008-01-07
Will I get an answer on this or will I have to reinstall?

---

### Post by jhvillegas2 on 2008-01-07
never mind

---

