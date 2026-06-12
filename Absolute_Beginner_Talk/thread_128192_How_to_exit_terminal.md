---
title: "How to exit terminal"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by napsilan on 2006-02-10
Admitedly this is a horribly newbie question, but...


After hitting alt+ctrl+f1 and getting into the full screen terminal, how do you get back to ubuntu/gnome?  

I'm sure it's a simple command, i've tried startx, but it said already active.  Exit just sends me to the text line login.

---

### Post by DevilsAdvocate on 2006-02-10
alt+ctrl+f7

---

### Post by engla on 2006-02-10
F1 to F6 are text terminals, and the X session normally lands on F7 because of this. If you lock your screen and log in as another user, you open a new session on F8, so you can switch between the two with alt+ctrl+F7 and alt+ctrl+F8. Cool, huh?

---

### Post by bluevoodoo1 on 2006-02-10
[QUOTE=napsilan]Admitedly this is a horribly newbie question, but...


After hitting alt+ctrl+f1 and getting into the full screen terminal, how do you get back to ubuntu/gnome?  

I'm sure it's a simple command, i've tried startx, but it said already active.  Exit just sends me to the text line login.[/QUOTE]

sudo /etc/init.d/gdm restart

---

