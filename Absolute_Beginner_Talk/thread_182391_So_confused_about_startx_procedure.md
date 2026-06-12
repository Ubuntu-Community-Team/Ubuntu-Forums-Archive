---
title: "So confused about startx procedure"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by mellibra on 2006-05-26
Some configuration files such as .xinitrc, Xsession really confuse me. Could someone explain how Linux use these files after startx? Thanks.

---

### Post by TheGimp on 2006-05-26
Are you trying to get a graphical interface? and did you install the full verison?

---

### Post by uzi09 on 2006-05-26
correct me if i'm wrong here since the same exact questions plagued me, and with *little* research this is what i found:

there are a few different display managers that run you're X sessions. we got gdm (gnome display manager) that ubuntu uses, xdm (the original X display manager) and also kdm. i'm sure there are probably others as well, but idk bout em.

they basically control your session (each time you login and use the gui for linux). 

.xinitrc and .xsession are both files that are used by xdm. i believe xsession is the file that runs stuff. usually you add in here which window manager or desktop environment you'd like it to run the next time you log in.

xinitrc is apparently used for:
"The xinit program is used to start the X Window System server and a first client program on systems that cannot start X directly from /etc/init or in environments that use multiple window systems.

If no specific client program is given on the command line, xinit will look for a file in the user's home directory called .xinitrc to run as a shell script to start up client programs. " ([https://engineering.purdue.edu/ECN/Resources/KnowledgeBase/Docs/20020202104528](https://engineering.purdue.edu/ECN/Resources/KnowledgeBase/Docs/20020202104528))

---

### Post by mellibra on 2006-05-27
Thanks

---

