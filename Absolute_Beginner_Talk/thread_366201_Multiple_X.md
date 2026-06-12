---
title: "Multiple X"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by gillespie on 2007-02-20
Hi all

I was wondering, is there a way that i can run multiple X sessions on different virtual terminals? Just out of curiosity...

Tom

---

### Post by marceloshima on 2007-02-21
> **gillespie said:**
> Hi all

I was wondering, is there a way that i can run multiple X sessions on different virtual terminals? Just out of curiosity...

Tom

What kind of virtual terminal?
If it's inside another X you should use xnest or xephyr

If it's ctrl+alt+fx vt you should execute X :n on a terminal.

n is the number for the vt.

---

### Post by napzilla on 2007-02-23
I know it's possible--I was even doing it earlier. I was running Gnome in slot 7 (ctrl+alt+f7), and I was running Kubuntu in slot 8. All I had to do was un-comment the following line in my /etc/X11/gdm/gdm.conf file (it was line 537, under servers, near the end of the file):
1=Standard
Keep 0=Standard un-commented, too. To the best of my knowledge, this means that you're telling gdm to launch an X server in the terminal at slot 8, too.

Unfortunately, I must add a disclaimer. My system recently decided to stop launching an X server in slot 8, and I'm not sure why. I don't think that the gdm.conf file is wrong; I think that it's some other bug. On the other hand, it may be that adding 1=Standard is not a stable approach. I'll let you know if I discover more.

---

### Post by chavo on 2007-02-23
Kdm will let you start a new session from the KDE menu. I know gdm has this capability but not sure if it's in the gnome menus. There is the fast-user-switching applet also that will allow you to do it. Alternatively you can hit ctrl-alt-F1, log in to the terminal and start x like this - startx -- :1, this will start a new x session. Just put whatever you want to start with x in ~/.xinitrc/, e.g. -> exec gnome-session to start a new gnome session.

Edit.. Once you start a new session the old session will be at tty7, so hit ctrl-altlF7 to go back to it and ctrl-alt-F8 to the new one.

---

