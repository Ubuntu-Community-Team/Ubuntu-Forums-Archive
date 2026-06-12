---
title: "graphics performance degradation"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Timaaaaaaay on 2007-02-20
hey all, i started running linux as a primary OS about a month ago, and have been quite happy until very recently.  it seems that my graphics are very laggy all of a sudden, though i havnt done anything to change configurations to my graphics card or drivers,  at least that i know of.  everything slows down to a crawl when i try to play anything with cedega, also when running anything graphically intensive, like project m (an xmms visualizer) and even if i have a number or webpages open or other applications with too much eyecandy.

i was wondering what could have caused this slowdown and if there is any way to fix it.  
specs if you need em, anything else you need to know just ask

radeon 9800pro 128 mb
1 gig ddr 3200 ram
amd athlon 2600+ barton core
gigabyte nforce 2 mobo

i would like to stress that the computer ran these apps not that long ago perfectly well.

---

### Post by terdon on 2007-02-20
An easy thing to try is to run the command "top" from a terminal, this will show you what is eating up your resources. wait till your machine slows down and then  run top, if there is anything using a very high percentage of the cpu post it here.

good luck

---

### Post by Timaaaaaaay on 2007-02-21
xorg seems to be sucking up everything free while running xmms projectm, and when i do any\thing with cedega.

---

### Post by igknighted on 2007-02-21
What is the result of "fglrinfo"?  Perhaps the recent kernel update messed up your 3d acceleration.

---

### Post by Timaaaaaaay on 2007-02-21
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

i need to reinstall the drivers dont i.

---

### Post by igknighted on 2007-02-21
> **Timaaaaaaay said:**
> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

i need to reinstall the drivers dont i.

That depends, how did you install them?  If you installed via the repo's it should be in your updates,  If you installed via envy, just run it again.  If you installed from the ATI site, there is a way to rebuild the module without reinstalling, but I cannot find it on the ATI site at the moment.  Your best bet (unless you want to keep searching for the rebuild command) is to follow ATI's uninstall instructions.  Then install the drivers from the Ubuntu repo's (sudo aptitude install xorg-drivers-fglrx) and then run the commands ATI recommends on the install page (the same that has the uninstall instructions).

---

