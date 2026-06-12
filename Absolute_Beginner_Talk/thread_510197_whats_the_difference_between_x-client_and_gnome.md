---
title: "whats the difference between x-client and gnome?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Pttyboy 92 on 2007-07-26
if I ever had to choose for some reason, what's the difference between the xclient script and gnome? And what is the default "session" for Ubuntu?

---

### Post by Pttyboy 92 on 2007-07-26
bump

---

### Post by Lexyboy on 2007-07-26
AFAIAA the X-client is the underlying windowing system, common to pretty much all the operating environments.  GNOME is the operating environment which provides you with your icons and general desktop type funcionality, and runs on top of X.

---

### Post by jsr on 2007-07-26
> **Pttyboy 92 said:**
> if I ever had to choose for some reason, what's the difference between the xclient script and gnome? And what is the default "session" for Ubuntu?

X Client - Is _any_ XWindow application like the xclock, xman, gcalc etc etc..... 
X Server - Is the X Window server which all the clients talk to. by using Xevent

Gnome - Is a Window Manager (more like an desktop environment) which gives the borders to the clients (windows) resize, move functions (the basic functions) + loads of more goodies that gnome has (icons, desktop widgets a development API )

XServer -> XProtocol -> Xlib -> Gnome 

I am not sure if that make sense to you!

---

### Post by Salazar420 on 2008-02-25
> **jsr said:**
> X Client - Is _any_ XWindow application like the xclock, xman, gcalc etc etc..... 
X Server - Is the X Window server which all the clients talk to. by using Xevent

Gnome - Is a Window Manager (more like an desktop environment) which gives the borders to the clients (windows) resize, move functions (the basic functions) + loads of more goodies that gnome has (icons, desktop widgets a development API )

XServer -> XProtocol -> Xlib -> Gnome 

I am not sure if that make sense to you!

Makes absolutely no sense whatsoever; to me, at least. Perhaps if you ditched the laymen-directed explanation I'd have more a chance at comprehension... thanks anyway, though....

---

