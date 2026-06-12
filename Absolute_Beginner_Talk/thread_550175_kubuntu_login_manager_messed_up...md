---
title: "kubuntu login manager messed up.."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by linkagge on 2007-09-13
I've had kubuntu running for a few days now and last night i turned the PC on and it brings up the login manager for KDE, i put in my username and password and the screen goes blank for a second then comes back to the login screen, i'm able to ALT+CRTL+F1 and login to the terminal. I haven't changed anything since it was last working, does anyone have any helpfull things that I could try to get this working again?

I would just reload the entire system because I really haven't done much except i've gotten LinuxMCE running and that took about 12 hours to get installed.

Thanks !
Chris

---

### Post by por100pre1 on 2007-09-13
Try this first:

```
sudo dpkg-reconfigure kdm
```

---

### Post by linkagge on 2007-09-13
I've tried that and no good, the command appears to run then I get back to the prompt. 

Is it supposed to prompt me for any input or just kinda do its thing?

I have also gone to the prompt and removed kdm, and kubuntu-desktop with typeing
sudo apt-get remove kdm
and
sudo apt-get remove kubuntu-desktop

then started up X, I did get an X window so i know that X is still working, then shut down X 

and reinstalled KDM and the Kubuntu-Desktop packages.

It's still doing the same thing as before though, login and black screen for a second then back to the login prompt.

---

### Post by linkagge on 2007-09-14
nobody else has any insight here on this problem for me ?

---

### Post by jfbilodeau on 2007-10-16
I'm currently experiencing this problem as well... Has anyone found a solution?

---

### Post by jfbilodeau on 2007-10-17
Solved -- I ran out of room on my /home partition.

That was an annoying problem, since the logs were silent about the problem. GDM allowed me to log in, and then reported the problem.

---

