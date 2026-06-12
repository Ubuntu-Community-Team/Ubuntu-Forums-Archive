---
title: "Ubuntu on MacBook vs. KDE on OS X"
date: 2008-07-12
forum: Apple Hardware Users
---

### Post by kramer2718 on 2008-07-12
Hi.  I have an Ubuntu box (AMD 64 x2 custom built) with KDE and love it.  I also have MacBook (about 2 GHz core2 duo cpu with 1 GB RAm--new nice machine) and hate it.  It's not that the MacBook performs badly.  It's plenty fast and responsive even with all those animated GUI things.  I just HATE the interface.  It has gotten to the point where I use it less because I hate it (point of ilustration:  in the Mac user administration thing, to add a new use, you have to click a + at the bottom of the screen--there's no add user button).  

Anyway, I am totally digging KDE, so I think that I'd like to put it on my laptop.  So here's the question: should I ditch OS X entirely and put kubuntu on it or should I just run KDE on top of the Mac OS X kernel?

On the one hand, I'm pretty familiar with Linux (I program on it at work), so I just feel more comfortable.  On the other hand, drivers could be something of an issue.  Also, then I would not have all of those Mac apps available (Time Machine is pretty nice + I'd have to figure out the Linux solution for syncing my iPod).  Also, the Mac kernel seems to be pretty sweet.  It's plenty responsive and boots up very quickly.

Anyway, I'd love to hear what others have to say about this issue.  Which solution is more difficult to install?  How hard is it to get those drivers to work?  Is it possible to get native OS X working under Ubuntu? Are there any other tradeoffs one can think of?

So what do you guys think?

---

### Post by joninkrakow on 2008-07-12
Well, I'm doing both on my PPC Mac. I run KDE 3.5.7 under X11 under OSX, using a helper app for launching it. I got it at [http://homepage.mac.com/rwikoff/slicedapple/KDELauncher.html/](http://homepage.mac.com/rwikoff/slicedapple/KDELauncher.html/)

My thoughts are this. You need to go look at the packages available at darwinports or fink, to see if they have all the software you need. Also, be prepared to be using older versions of most applications. These "distros" are entirely volunteer, and they don't update as fast as Ubuntu. Also, there is a vast disparity between what's available on these "distros" vs. Ubuntu. 

Also, if you go the Fink or darwinports route, ports or fink will have to compile _everything_ from source! That could take a while. However, you do have the benefit of using kde rootless in OSX, or rooted, or even weirder, at the login screen, type >console and get KDE full-screen (so saying you've configured your .xinitrc or .xsessions file correctly. Actually, typing >console at the login screen gives you a full-screen commandline system, and you will have to launch X yourself. I have yet to find a gracefull way out of this however. 

Another option is to find an older version of Darwin, install that, and compile port or fink, and start from a simple, commandline install.

All that said, it might be easier to simply load Ubuntu, and have one of the most expensive Ubuntu boxes possible. ;-) You could also dual-boot. Which is what I do. Or, you could get used to the differences of OSX.

Oh, I almost forgot. If you are running Leopard, make sure that darwinports or Fink will work. Lots of things for X11 broke with Leopard.... yet another reason to go Ubuntu.

-Jon

---

### Post by kramer2718 on 2008-07-12
If I run KDE on OS X, will I be able to sun Safari (not that I'd want to) or iTunes or TimeMachine or whatever natice Darwin apps?

---

### Post by cyberdork33 on 2008-07-12
I messed with some of the KDE apps on OSX. It was quite nice. They are still very buggy though.

---

