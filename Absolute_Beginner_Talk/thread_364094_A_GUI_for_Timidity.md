---
title: "A GUI for Timidity?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-02-17
Hi! I hope I spelled the name of the program right.  What I am talking about is the nifty console program that plays midi files.  Now, is there any way to get some sort of GUI up and running so that I can control what part of the song is playing?

---

### Post by luibh on 2007-02-17
```
timidity -ig
```

That should launch the GTK gui.

---

### Post by Darklighter137 on 2007-02-17
That failed, it said no such commad -gi existed. =(

---

### Post by Maestro23 on 2007-02-17
> **Darklighter137 said:**
> That failed, it said no such commad -gi existed. =(

Did you type: timidity -ig

or 

timidity -gi
?

---

### Post by luibh on 2007-02-17
I installed the package timidity-interfaces-extra, that may include the GTK GUI. I'm not totally sure.

---

### Post by tbroderick on 2007-02-17
install timidity-interfaces-extra

---

### Post by Darklighter137 on 2007-02-17
Thanks guys!  The installation of the new package and typing the i and the g in the right order fixed things up. =)

---

### Post by mimsmall on 2007-03-20
I have an icon in Applications>SoundandVideo>Timidity but when I click on it Timidity does not open. Entering Timidity -ig in a terminal opens the gui. How can I get the gui to open when I click on the icon?

---

### Post by klytu on 2007-04-13
> **mimsmall said:**
> I have an icon in Applications>SoundandVideo>Timidity but when I click on it Timidity does not open. Entering Timidity -ig in a terminal opens the gui. How can I get the gui to open when I click on the icon?

In Gnome, right-click a .mid file.  Select "open with other application", scroll down for TiMidity++ and select that. Or if you really want the same interface you get with timidity -ig, click "use a custom command" after selecting "open with other application" as above and type in > /usr/bin/timidity -ig

---

