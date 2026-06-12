---
title: "Compiz Problem"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by thecresta on 2006-09-17
Hi All,

I've had Ubuntu installed for a week now and have had to re-install already, but I think I'm getting the hang of it now :rolleyes: 

I've installed NVIDIA Compiz, but I'm having a few mouse problems. A right mouse click zooms - making the usual right-click menus hard to get to, and the wheel scroll does a similar thing - scroll up and it zooms in, scroll down and the page scrolls down!  :confused: 

I think I know where to fix this - the Compiz Settings Manager - but I can't get to it! The shortcut in the System>Settings menu does nothing, and when I type 'csm' into the terminal it brings up the following error:

csm: error while loading shared libraries: libdbus-1.so.3: cannot open shared object file: No such file or directory

*Ive checked in /etc/usr/lib/ and the file isn't there, but I can't find it on the net!*

I'm sorry it's a bit specific. :roll: I hope somebody can help. 

Cheers
TCS

---

### Post by JayTee on 2006-09-17
There are several How-tos on this forum for installing XGL and Compiz. I'd do a search and read several before you go any further. The lib files you need are not part of the default Ubuntu install and are not on the standard Repositories. You'll need to add the sites that host them to your sources.lst file and from the advanced mode in Add/Remove programs on the Settings menu choose Repositories and enable all the ones not checked. Then just do a search for the lib file.

---

