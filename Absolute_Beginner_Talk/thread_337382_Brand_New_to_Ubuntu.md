---
title: "Brand New to Ubuntu"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by dphoenixa on 2007-01-12
A buddy of mine put ubuntu on my computer and we finally got everything working perfectly just the other night. But tonight I just pluged everything in, in my room and suddenly right after the loading screen it's goes black. I press the power button and it gets to the loading screen again and just shuts off. I have no idea what to do. If you can please help me.

---

### Post by BarfBag on 2007-01-12
Sounds like X doesn't want to start.  When you get to the Grub menu, go into recovery mode.  Once it's done loading, type:

> startx

---

### Post by dphoenixa on 2007-01-12
what is the Grub menu and how do you get into recovery mode.

---

### Post by jas0 on 2007-01-12
You setup the computer in a different location using different mouse/keyboard/monitor? Also, what all are you pluggin into your box before starting it.

Try unplugging everything but the mouse/keyboard/monitor. If that doesn't work, try a second monitor (if you have one).

---

### Post by dphoenixa on 2007-01-12
that is correct. All I have is the mouse/keyboard/monitor plugged in. If I plug in a different monitor what would/could be the difference between the two different monitors.

---

### Post by jas0 on 2007-01-12
Your monitor may not support the X11 options you guys configured. 

When the monitor shuts off, do you see your hard drive light blinking on and off for a while?

---

### Post by dphoenixa on 2007-01-13
Yes it does. It's very dim but it does.

---

### Post by BarfBag on 2007-01-13
The Grub menu is the list that comes up before Ubuntu boots.  The thing with the timer.  To get into recovery mode, use the arrow keys to move down to it on that list.  You'll see a lot of things flash (this is what happens under the Ubuntu logo and the progress bar).  Eventually, you'll see a text-based log-in.  Type in your user name and password, then type:

> startx

---

### Post by dphoenixa on 2007-01-13
Okay I am loged in and it is sayng i am not authorized to run the X server, aborting. xinit: server error

---

### Post by sloggerkhan on 2007-01-13
type startx and see if it works from that screen.

---

### Post by dphoenixa on 2007-01-13
that is what it said when i typed startx.

X: user not authorized to run X sercer, aborting.
giving up.
xinit: connection refused(errno 111: unable to connect to X server
xinit: no such process (errno 3): sever error

---

### Post by sloggerkhan on 2007-01-14
If that's what it says when you are root, I have no idea.

---

### Post by floke on 2007-01-14
how about using 'sudo startx'
(I know the user should have root privileges anyway but I've had things happen to my user privileges before when things have gotten borked so its possible that the user is no longer root and must use sudo - just a thought)

Also - you could possibly try

sudo dpkg-reconfigure -phigh xserver-xorg

Which I think will allow you to redo the X settings (although I could be completely wrong on this. Lets face it though, at this stage it won't exactly hurt!)

Hope any of this is of some use.

---

