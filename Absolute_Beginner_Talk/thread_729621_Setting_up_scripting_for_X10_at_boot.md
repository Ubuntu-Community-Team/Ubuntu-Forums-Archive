---
title: "Setting up scripting for X10 at boot"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by HuskyPups on 2008-03-20
[FONT="Comic Sans MS"][SIZE="3"]Hello:

A real noobie here, been using Ubuntu 7.10 for all of a week now. LOVE it=D>

I use X10 to turn on/off my routers and modem and keep the electric bill lower (cheap so and so here). I'm wondering if I can setup some kind of 'startup script' to turn things on when the computer boots, but before the login screen. I read somewhere about bottlerocket using a command line interface so I'm thinking that I 'should' be able to call it from a script or something similar while booting. The problem is, I know just enough about Linux in general, and Ubuntu in particular, to be dangerous to myself and others.......and the last time I worked with a command prompt was a llloooonnnnnggg time ago.

Would some one be kind enough to point me in the correct direction so I don't hurt myself?? Would rather not learn by having to reinstall everything over and over :roll:

The equipment I have to use for this is:

1 cm17a
or 
1 cm11 (if I get off my lazy butt and run wiring for it)

And just for the heck of it:

3 wallwarts @ 12 watts each = 864 watts per day
2,5920 watts per month or about $0.36 (told you I was cheap)

Not much when you thing about it, but every little bit helps.

All this cause I'm too lazy to press one little remote control button..........shesh#-o


Thanks for taking the time to read my babbling

David and the Mutts

 [/SIZE][/FONT]

---

### Post by jordanmthomas on 2008-03-20
Anything you put in /etc/rc.local will be run at boot.

As for WHAT you should put in there, I have no clue.  All I could gather is that you run some script to turn off your stuff.

---

### Post by HuskyPups on 2008-03-20
Thanks for the quick response.

Here is the description from the BottleRocket web site:

*BottleRocket is a command-line interface for Unix systems to use the FireCracker kit. It is easy to use, has all of the major (non-gui) functionality of the Windows interface, is easy to call from scripts and the backend code is made to be easily linked into other programs.*

I know nothing about scripting, so what I'm looking for is some idea of where to begin. The website doesn't go into detail about where to put what so I'm lost..........

Have a good day

David and the Mutts

---

