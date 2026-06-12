---
title: "Startup Problem"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by GeneralHooHa on 2008-02-06
I have gutsy gibbon. When it starts up and gets to "Starting Gnome Display Manager" or something like that, the screen switches to tty7 and shows a loading cursor for about 10 seconds. Then it goes back to the messages, which now say running local boot scripts, then goes to tty8 and loads gnome normally. I don't know what I did to make it do this, but its not a problem with tty7 (I've tried forcing it to start on different ones). This takes a lot of time. How can I have it go directly to gnome?

---

### Post by marufaberlin on 2008-02-07
You don't want a login Manager? No Passwords? Nothing like that at all?

---

### Post by marufaberlin on 2008-02-07
To run Gnome, you must be logged in as some user. If GDM logs you in as one automatically, you don't need to worry about logging in. (Technically, GDM is started as a user called daemon). But if you edit your /etc/X11/xorg.conf to start gnome and put startx into your .bashrc (if you use bash), disable the GDM service, then you should be able to log in from the terminal and go directly to gnome.

---

### Post by GeneralHooHa on 2008-02-07
Sorry, I worded this wrong. It loads, goes to a black screen for ten seconds, goes back to the bootup messages (I don't have usplash), and then goes to the login screen. It should go directly to the login screen when it's done loading. It shouldn't go to a black screen then back to the messages then to the login screen.

---

### Post by GeneralHooHa on 2008-02-08
Bump

---

