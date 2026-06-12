---
title: "Running graphical applications without desktop running? Linux dependency on desktop?"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by eepiccolo on 2005-07-27
Hello,

If I boot into a terminal (no desktop is loaded), will I still be able to run graphical applications?  Specifically, I'm interested in a game called Stepmania.  I can run it while running KDE, but I want to see if it runs faster/smoother with no desktop.  It does, however, already run much, much smoother that it did on WinXP.

And my other question, if I set an application (again, Stepmania)  to run at startup using the GUIs provided by KDE (system options or whatever it is), will that application still run if I boot with no desktop?

Oh, and is the best way to boot into a terminal to reduce the run level I boot into?

Thanks for any help!

---

### Post by poofyhairguy on 2005-07-27
[QUOTE=eepiccolo]Hello,

If I boot into a terminal (no desktop is loaded), will I still be able to run graphical applications?  [/QUOTE]


Nope. you need the xserver to run graphical apps. The only easy way to run the xserver is through a desktop.

---

### Post by varunus on 2005-07-27
The best way to boot into a terminal is to hit CONTROL-ALT-F1 at the login screen, log in at the ensuing text prompt, and execute the following command:

```

sudo /etc/init.d/gdm stop
--or for KDE, if the above doesn't work--
sudo /etc/init.d/gdm start
```

However, if you start a GUI from here, it will normally start KDE; you'll need to set up what's called an "Xsession" file if you want to boot up a custom environment.

A much simpler solution:

Open a terminal, and type
```
sudo apt-get install twm
```

Then, select "failsafe xterm" from the "sessions" menu at the login screen when you want to play stepmania.  Type the following:
```
twm&
stepmania (or whatever command starts it)
```

---

