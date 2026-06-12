---
title: "Too slow"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by dalani on 2005-10-18
I installed Ubuntu 5.04 on my Intel PII in dual boot w/ Win98SE
and to my surprise all apps and operations on Linux run and startup much slower especially Firefox, even Gedit.  How do I spped up the processor

---

### Post by Leif on 2005-10-18
switch to a lighter desktop than gnome. try xfce, fluxbox, openbox or icewm. you can install them through synaptic. afterwards, logout, choose from sessions, and login again

---

### Post by bluefrog on 2005-10-18
What's your RAM on that box? 
64   will be very, very, very slow 
128 will be very slow
256 will be fine

---

### Post by dalani on 2005-10-19
[QUOTE=bluefrog]What's your RAM on that box? 
64   will be very, very, very slow 
128 will be very slow
256 will be fine[/QUOTE]


I have the same amount of mem available in both OS: 96meg

Is the problem gnome? When I activate my file browser, or start up Open Office, it takes forever to open. Lots of disk thrashing when multitasking and sysyem monitor shows my CPU maxed out at 100% quite often. Meanwhile with Win98SE it's slick fast in comparison (i know I should not compare).

My question is it that the distro was optimized for faster Intel processors? 

In the meantime can uninstall gnome completly and install ICEworm without ill effects?
Will evolution if Gnome is removed?

---

### Post by dbott67 on 2005-10-19
It won't really matter which DE/WM you use if you're going to be using Firefox or OpenOffice.  Your best bet is to add more RAM (at least upgrade to 256).

The other lightweight WMs out there (fluxbox, ICEwm, Enlightenment, etc) all run nicely on machines with low RAM, but as soon as you try to do something with some heavyweight apps (i.e. Firefox, Gimp, OOo, etc.) your computer's RAM will max out.

The default Ubuntu installation may include some other apps & services that you might not want in order to keep memory consumption down.  You could try an 'expert' installation and only choose those items that are critical for your application.

I have a slower computer running Ubuntu (P2-300, 256 MB RAM) and am using Gnome.  I tried virtually all the other DEs & WMs, but they all consumed at least 128 MB of RAM with no apps running (other than the default Ubuntu installation provides).  When I switched to Opera for browsing, my computer responded much quicker than with FF.  Epiphany is also faster than FF, but in my experience Opera is faster.

As for OpenOffice, you can try AbiWord and other 'lighter' apps to speed things up.

-Dave

---

### Post by dalani on 2005-10-19
Thanks for the tips: 
I have epiphany on my  install disk so I will switch to that browser. All reports indicates FF is slow.  I will stick to Gnome (I do like my distros in mint condition). Instead turning the anti-aliasing OFF should  speed things up (there is a thread about that somewhere by Azz).

---

