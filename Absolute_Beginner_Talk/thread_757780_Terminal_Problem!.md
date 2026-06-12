---
title: "Terminal Problem!"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Snoo on 2008-04-17
Hi there,
Can anybody help...?

I've just done a Xubuntu install (latest version). However whenever I try to open Terminal to do some command line stuff, the screen goes funny and it boots me out into the login screen.

Any ideas?

Thanks.

---

### Post by Hendrixski on 2008-04-17
That's odd. What are you doing to get to the terminal?

if you're hitting ctrl alt f1 then... well, yeah, it would seem like you're logged out.  ctrl alt f7 would fix that.

I've never had a program crash that logged me out.

---

### Post by Snoo on 2008-04-17
> **Hendrixski said:**
> That's odd. What are you doing to get to the terminal?

.
Applications>Accessories>Terminal


.. from up in the menu.

How do I open and Xterm window instead?

Also it is the GUI log-in screen, not the textbased log-in.

---

### Post by Hendrixski on 2008-04-17
hhmm. strange.
now you said the latest version: is that 7.10 aka "Gutsy Gibbon" which came out 6 months ago, or is it 8.04 "Hardy Heron" which comes out in 7 days.  Because if you installed the beta then that is a bug that you should totally report.

Also, you did install all the updates right?  Because that would most likely have been fixed in an update somewhere.

And... lastly, you didn't change the commands on any of the menu items? no?  Do any of the other menu items do the same thing or just terminal?  Does it look like a normal logout, or does it look like everything crashes?

Lots of questions, but we'll get to the bottom of this! :-)

---

### Post by Snoo on 2008-04-17
Am running Gusty Gibbon (Xubuntu).

System is all up to date with updates (Just double checked). Haven't changed any menu item commands to my knowledge. Haven't really done much with the system at all. Only noticed this because I was getting into installing flash player which needed the command line.

---

### Post by Hendrixski on 2008-04-17
> **Snoo said:**
> Am running Gusty Gibbon (Xubuntu).

System is all up to date with updates (Just double checked). Haven't changed any menu item commands to my knowledge. Haven't really done much with the system at all. Only noticed this because I was getting into installing flash player which needed the command line.

Crap.  that pretty much eliminates all of my theories of what could have gone wrong.  Perhaps you should just try a different desktop? You can
```
 sudo apt-get install ubunt-desktop 
```
and it will install gnome for you. or kubuntu-desktop for KDE.
or try some other window managers like iceWN (which is what they use on the new eeePC's)  or OpenBox, or (if you're a complete minimalist) ratpoison.
Since you can't open a terminal try hitting CTRL ALT F1 and that takes you to a non-GUI login screen, and you can use that as the "terminal" until another one installs... and the terminal on one of those should work.

That's the best I can offer for now.  hope that helps.

---

### Post by Snoo on 2008-04-17
OK. I've found out how to open Xterm. That seems to run fine.

A bit of googling shows this as a known bug (Don't know why updates haven't fixed it).

It's to do with setting the DefaultDepth (xorg.conf) from 24 to 16 for future reference.


Cheers for you help Hendrix.

---

