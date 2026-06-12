---
title: "newbie here"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by roblowe on 2005-12-15
Just installed ubuntu 5.10. Couple of hitches. The mouse is not reposnding. What am I missing?

How can I tell if I running either Gnome or KDE. 

I'm guessing I'll be able play arounda little bit more If the mouse works.
Here is the config.

Its a dell desktop with celeron III. 20 G hd 256 mb memory. Installation was breeze, let the installer do the partion for me and took all the dfault option. Still need to configure the network card. I'm guessing getting to mouse to work will help with a lot of this. Thanks for you input.

rob
PS: Installed linspire b4, but it felt like driving a sports car with auto trans. Wanted to be more involved with the operation. Hence the switch.

---

### Post by Zelut on 2005-12-15
I wont say what I think of Linspire <spit>...

Uhm, if you've got a taskbar top & bottom you're using GNOME.  Just one (similar to windows start menu) then you've got KDE.  Its a big battle over which is better so I wont get into that, but GNOME installs by default on the standard ubuntu installer.

About the mouse... is it ps2 or usb?  Plugged in securely? (simple, I know, but needed.)

---

### Post by bullfrog on 2005-12-15
if your mouse dont work try another one sometimes the pc dont like a certain mouse hope this helps  bulldog

---

### Post by roblowe on 2005-12-16
It tunrs out the mosue is actually active becos the right click works. The problem is with getting the cursor to move. 

The mouse I'm using is a optical mouse, ps2, GE brand.

rob

---

### Post by TeeAhr1 on 2005-12-16
Silly question: Was this the mouse you had plugged in when you installed?

---

### Post by GreyFox503 on 2005-12-17
You could try running the xserver configuration.  If you want to do this, hit Alt + F1, then go to Accessories > Terminal.

```
sudo dpkg-reconfigure xserver-xorg
```

This is a pretty generic config, so it will ask you a lot of questions about graphics, monitor, etc.  Leave it at the defaults if you're not sure.  Eventually, you get to some stuff about choosing mouse input, where you should pay attention and try to pick something to get your mouse working.

Best suggestion I can think of, because I've *never* had trouble getting a mouse working under Ubuntu, so I'm not sure where I'd start.

---

