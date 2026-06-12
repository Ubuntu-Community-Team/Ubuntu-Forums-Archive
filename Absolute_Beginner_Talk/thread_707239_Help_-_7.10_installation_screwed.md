---
title: "Help - 7.10 installation screwed"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-02-25
So I got a 7.10 Live CD working fine and dandy.
It had no errors when I did a CD check, 
and the Live session seemed to work fine,
so I installed it...

But then after restart it was messed up...
The main boot screen loaded but then it went into text mode,
and now there is a bunch of white (and a tad of orange) manged lines shivering in the center of the screen.

I assumed it was on the login screen so I typed my user name, hit enter (seemed ot change some things), then typed my password and hit enter again (seemed to load another screen)
but it's still all mangled as hell

Is there a problem with the graffics drivers perhaps?

---

### Post by overdrank on 2008-02-25
> **Xarok said:**
> So I got a 7.10 Live CD working fine and dandy.
It had no errors when I did a CD check, 
and the Live session seemed to work fine,
so I installed it...

But then after restart it was messed up...
The main boot screen loaded but then it went into text mode,
and now there is a bunch of white (and a tad of orange) manged lines shivering in the center of the screen.

I assumed it was on the login screen so I typed my user name, hit enter (seemed ot change some things), then typed my password and hit enter again (seemed to load another screen)
but it's still all mangled as hell

Is there a problem with the graffics drivers perhaps?

HI and what is the model of the graphics card? You can try and reconfigure your xorg use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then use the command reboot.

---

### Post by Xarok on 2008-02-25
> **overdrank said:**
> HI and what is the model of the graphics card? You can try and reconfigure your xorg use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then use the command reboot.

It's an Emachines T1090 and I  think has a "Intel DirectAGP 3D graphics adapter"

I pressed Crt + Alt + F1 and it was loading in text mode, but when it got to "running local bootscirpts"
it started flashing and when back to the same crap.

---

### Post by jonabyte on 2008-02-25
You probably don't want to hear this, but you may want to try 7.04 first. I have had many problems with 7.10 on my machines.

---

