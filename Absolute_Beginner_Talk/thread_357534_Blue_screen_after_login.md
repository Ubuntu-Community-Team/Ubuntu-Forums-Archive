---
title: "Blue screen after login"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by amphet on 2007-02-09
Hi all,

I was changing my wireless settings everything went fine until I rebooted, now after the login all I get is a blue screen with a terminal like shape in the left side of the screen and gets stuck there, I'm on Edgy running GNOME.

Any ideas?

---

### Post by taurus on 2007-02-09
Log in with your username and password and see what happens when you run this command at the prompt?

```
startx
```

---

### Post by amphet on 2007-02-09
it says that it's already running, I tried using failsafe but with the same results

---

### Post by taurus on 2007-02-09
What's the output of this command from a terminal?

```
ps -A
```
Also, try pressing <Alt>F7 to see if you can get to a GUI login screen.

---

### Post by amphet on 2007-02-09
I get to login in GNOME's GUI after that when the desktop is supposed to load is when I get the blue screen.

---

### Post by kbsuperstar on 2007-02-09
```
sudo dpkg-reconfigure xserver-xorg
```

Just reselect your settings

---

### Post by amphet on 2007-02-09
> **kbsuperstar said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```

Just reselect your settings

already tried that with no luck :(

---

### Post by amphet on 2007-02-09
this is the exact problem I have, but unlike that guy I never installed network-manager

[http://www.ubuntuforums.org/showthread.php?t=305413&highlight=login+blue+screen]("http://www.ubuntuforums.org/showthread.php?t=305413&highlight=login+blue+screen")

---

### Post by taurus on 2007-02-09
Do you have the LiveCD and can you boot your machine up with the LiveCD?

---

### Post by amphet on 2007-02-10
I sort of  fixed it by switching to KDE now everything is working fine, maybe it's a GNOME issue?

---

