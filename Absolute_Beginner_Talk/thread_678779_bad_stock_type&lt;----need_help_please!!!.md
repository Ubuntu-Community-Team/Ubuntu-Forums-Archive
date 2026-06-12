---
title: "bad stock type&lt;----need help please!!!"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by luschka_monroe on 2008-01-26
i just installed ubuntu in my laptop yesterday...and because i was new to using ubuntu that i try tweaking my desktop and adding some new theme. there's this one particular theme (it's a login screen) that i've installed. after i reboot my computer to see how it looks...i've got a message unable to launch light coffee---bad stock type..so the ubuntu launch a random login screen but the problem is i can't seem to type my username and password...can someone help me with this??? i'll appreciate any help!!!

thanks in advance!!!

---

### Post by taurus on 2008-01-26
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, stop the GUI login screen so you can start Gnome.

```
sudo /etc/init.d/gdm stop
startx
```
Now, change back to the default GUI login screen.

---

### Post by luschka_monroe on 2008-01-26
> **taurus said:**
> Press <Ctrl><Alt>F2 and log in with your username and password.  Then, stop the GUI login screen so you can start Gnome.

```
sudo /etc/init.d/gdm stop
startx
```
Now, change back to the default GUI login screen.


**thank you **so much for your help!!! 

can i know what a bad stock type message mean?? does this mean i can't just install new themes for my desktop???

---

