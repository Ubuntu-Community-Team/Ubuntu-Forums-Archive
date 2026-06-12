---
title: "restart x"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by alvid on 2006-09-15
I just updated my nvidia driver and terminal message says i have to
restart "x' to take effect. 
what is the command to restart "x" ??
Thanks,
alvid

---

### Post by Punk-Piranha on 2006-09-15
Press Crtl+Alt+Backspace
Or reboot the machine :p

---

### Post by oedipuss on 2006-09-15
You can kill the current X server by pressing Alt+Ctrl+Backspace. It should restart by itself. If it doesn't, and goes to a terminal login, log in , and type :

sudo /etc/init.d/gdm stop
It should report that gmd stopped ok,and then
sudo /etc/init.d/gdm start

---

### Post by alvid on 2006-09-15
Thanks for the help!!
Alvid

---

