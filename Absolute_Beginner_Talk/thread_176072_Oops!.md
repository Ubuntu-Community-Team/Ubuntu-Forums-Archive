---
title: "Oops!"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by CybaCowboy on 2006-05-14
**I just deleted my entire GUI!**

After downloading KDE, I was trying to remove everything that was related to GNOME and, well I *completely* lost my GUI!


Anyway, I worked out that I can still login, although it's like the gold 'ol MS-DOS days, putting me in Terminal once I've entered my username and password...


My question to you is if I can login, I *should* be able to type a Terminal command to download KDE and make it the default interface, right?

If so, how?

---

### Post by mostwanted on 2006-05-14
Try reinstalling gdm.

---

### Post by CybaCowboy on 2006-05-14
How?

What's the Terminal command?

---

### Post by gingermark on 2006-05-14
[QUOTE=CybaCowboy]**I just deleted my entire GUI!**

After downloading KDE, I was trying to remove everything that was related to GNOME and, well I *completely* lost my GUI!


Anyway, I worked out that I can still login, although it's like the gold 'ol MS-DOS days, putting me in Terminal once I've entered my username and password...


My question to you is if I can login, I *should* be able to type a Terminal command to download KDE and make it the default interface, right?

If so, how?[/QUOTE]
do ```
sudo apt-get install kubuntu-desktop
``` If you are asked to choose between KDM and GDM choose KDM (assuming you want KDE, and want to remove GNOME later, which it appears you do)

---

### Post by Sef on 2006-05-14
```
sudo apt-get update

sudo aptitude install kubuntu-desktop
```

---

### Post by CybaCowboy on 2006-05-14
Well I got KDE installed... So how do I set it to load by default on booting the computer (as opposed to Terminal loading by default)?

[i]Edit:
After rebooting, I see that it has forced itself to be the default automatically!

Thank you for all your help peoples![/i]

---

### Post by skippy81 on 2006-05-14
> sudo dpkg-reconfigure gdm

try running this and selecting the kdm option.  Also explain what happens when you boot.  Do you get any sort of graphical interface? or do you just get dumped at a 'command prompt'?

If you are starting in terminal mode, you should be able to use "startx" to get you into the gui.  From there I would recommend using synaptic and reinstalling either kubuntu-desktop or ubuntu-desktop packages.   If you allready have them installed, just reinstall them.  Then do another > sudo dpkg-reconfigure gdm and you should definately be able to boot into a gui.

---

