---
title: "Number of desktops on Ubuntu?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by ronoxQ on 2007-03-04
I don't know if desktops is the right word for it, but it's the one that I found on an FAQ.

I just installed Ubuntu, and I know what the two squares down at the bottom are for. (The ones for changing between different screens.) Is it possible to add more of those at once, so I could have, say, four rather than two?

Thanks for the help: loving Ubuntu so far.

---

### Post by wat3r on 2007-03-04
Right click one of the panels and press Preferences. Then select "Number of workspaces:" to the number you want.

---

### Post by pveith on 2007-03-04
Sure, you can have more of the goodies...

just right click the desktop-panel-applet and select properties. There should be all configuration you need to get more desktops...

---

### Post by freesitebuilder on 2007-03-04
How does using more than one desktop affect performance? I'm thinking about when I open too many programs in Windows, my PC eventually chokes and dies. :) Do I have to consider memory etc when using multiple desktops in Ubuntu?

---

### Post by pveith on 2007-03-04
Multiple desktop doesn't decrease performance significantly. Having a lot of open/running applications some how does. It largely depends on the type of application running. If you have 20 3d-demos running, your graphic-card will probaly start getting all dizzy ;). No seriously, in gerenal most programs don't decrease performance significantly on their own. Having programs, which are using the same resource, will make you suffer from a slideshow X.

So just put an the system-monitor applet in the panel and let it watch for processor usage and memory. As soon as one of the two gets filled up for a long period and you are noticing a performance lag, have a look at what is running (click on applet) and close one of the perfomance killers, you are not yusing at the time. After some time you will know, which programs should be closed and which can be left open...

Obvious candiates for performace-killers are rendering programs, cdparanoia (which makes intensive use of hardware reads), encoders (lame, oggenc. So decoding is not much trouble), but these will usually only eat performace when you want something from them. Then there are those programs like desktop-search (beagle), which try to decide when to work and when not. For these you have to decide in general, as beagle is not of much use if it is constantly down (startup and shutdown beagle are real perfomace killer) ...

---

### Post by ronoxQ on 2007-03-04
Thanks so much! Worked like a charm.

---

### Post by Henry Rayker on 2007-03-04
The number of desktops really shouldn't take from your system resources much (if at all). However, running a bunch of apps on each one can and will. Every single app you run will take up some amount (however small) of your system's resources (whether it be CPU cycles, physical RAM or virtual memory).

---

