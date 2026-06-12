---
title: "startx problems"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Vitaeboy on 2007-12-27
When I boot Ubuntu, I get the pretty little logo and the orange bar.  Then it asks me for my username and password.  I type my username and password and it logs me in, plays its logging in sound, and gives me a black screen with a cursor on it.  I can move the cursor, but that's about it, so I hit ctrl+alt+F1 and tell it to startx.  It dumps me right back on the black screen with my cursor.  If I try sudo startx it tells me it's 'waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.'

---

### Post by PmDematagoda on 2007-12-27
You should terminate the current X-Server session before starting another.

Press Alt+PrntScrn+I to terminate all the processes, then press Alt+PrntScrn+R and then press Ctrl+Alt+F1 that should bring you to a tty and you should be able to startx.

The keys given before are magic SysRq keys, more information on them can be found [here]("http://ubuntuforums.org/showthread.php?t=617349").

---

### Post by Vitaeboy on 2007-12-27
When I startx again it just sends me back to the black screen with cursor.

---

### Post by PmDematagoda on 2007-12-27
What are the specifications of your system?

---

### Post by Vitaeboy on 2007-12-27
Eep, I dunno.  It's whatever Dad had before the last time he upgraded...

---

### Post by PmDematagoda on 2007-12-27
Ok, while I realise that this is not a real fix, you can try using a different DE. When you get to a tty, execute:-

To install KDE:-
sudo aptitude install kubuntu-desktop
for a full Kubuntu DE. Or just:-
```
sudo aptitude install kde-core
```
for just the base applications.

To install Xfce:-
```
sudo aptitude install xubuntu-desktop
```
for a full Xubuntu DE. Or just:-```

sudo aptitude install xfce
```
for just the base applications.

---

