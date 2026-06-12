---
title: "graphics  problems on kubuntu"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Benifited on 2008-02-27
i was checking out the drivers on my kubuntu setup. and i changed the drivers to the ati (vesa)  to see if it would work better with the card. but after i restarted the computer the screen was messed up.the system starts but u can see anything. the screen is distorted but u can still see colors and the mouse move. how can i fix this problem?

---

### Post by taurus on 2008-02-27
Press <Ctrl><Alt>F2 and log in with your username and password.  Then at the prompt, reconfigure your X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Once it's done, get back to the GUI login screen with <Alt>F7 and restart X again with <Ctrl><Alt>Backspace.

---

### Post by chris.a.barker on 2008-02-27
1. Type control+alt+F1
2. Log in to your machine
3. Run this command.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
4. Reconfigure the Xserver.

Let us know if you have problems with this.

---

### Post by chris.a.barker on 2008-02-27
Nice job Taurus...Faster typer!

Cheers

---

### Post by Benifited on 2008-02-27
will this also work for a wubi setup? sry i forgot to mention that

---

### Post by Benifited on 2008-02-27
ok thx alot guys that worked im happy now yay!!

---

