---
title: "Ubuntu 6.10 on MacBook Pro - LiveCD X problem"
date: 2006-10-29
forum: Apple PPC Users
---

### Post by thecwin on 2006-10-29
When I try to boot the LiveCD on my MacBook Pro by holding option and selecting the CD at start, then choosing the first option on the boot menu, the splash scroller works fine until it tries to start X.

The display corrupts almost like you've opened a raw bitmap with the wrong settings (I'll attach an image to show what I mean). I'm guessing it controls the refresh rate badly or something else with the screen, but I'm completely in the dark about how the laptop screen is attached internally as well as how DVI works in Linux, if it is attached via DVI.

I'm going to try FC6 and see if it's an Ubuntu only problem.

Edgy's screen detection seems to have taken a step backwards... not one computer I've tried it on (nVidia and ATIs with LCDs attached via VGA) has worked straight out the box without messing with X configs. These computers worked fine on Dapper.

Attached is the output of system_profiler in OS X (Gzipped so it'd let me attach it)

---

### Post by Mars Cydonia on 2006-11-05
I have just tried to install Ubuntu 6.10 on my MacBook Pro 17 and even I have the same problem.
I have also tried to change the boot resolution but I ever get this problem and I can't install ubuntu.

---

### Post by thecwin on 2006-11-11
Well, Fedora Core 6 works fine (relatively speaking... I don't really like FC). Seems that this is an Ubuntu problem that noone seems to know the answer to...

---

