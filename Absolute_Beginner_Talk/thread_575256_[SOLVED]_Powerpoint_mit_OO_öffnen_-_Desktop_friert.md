---
title: "[SOLVED] Powerpoint mit OO öffnen - Desktop friert ein"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by perixx on 2007-10-13
I don't know what could be causing this:

usually, Open Office should open all Windows-Office formats without complaints, and this is true for Word-Documents and mostly for Excel-sheets.

Not so for .ppt / .pps-files from Powerpoint 2000 - opening these (actually PLAYING them) freezes the whole desktop; only Alt-F4 or Ctrl+Alt+Backspace can recover from this and end the hanging app. Desktop is back in a normal state after Alt-F4...


Anybody any idea :?

Thanks, 
perixx

---

### Post by LanDan on 2007-10-22
can you run it from the terminal and see if you can get more output?

ooimpress

---

### Post by perixx on 2007-10-22
Sorry, not currently - I broke the desktop by messing around with other repositories...

perixx

---

### Post by perixx on 2007-10-26
Back on track, LanDan!

I tried typing + starting 'ooffice' from the Terminal, loaded the presentation and started it... same effect, still.


perixx

---

### Post by ronmarley1 on 2007-10-26
Sorry for the non-answer, but you may have better luck with the OpenOffice.org forums at [http://www.oooforum.org/](http://www.oooforum.org/)

---

### Post by perixx on 2007-10-26
Well, I figured it might be a problem with Xubuntu's standard picture viewer not liking some picture formats used in the presentation (.bmp) - if it's used by OO at all....

But you're maybe right, I'll try it there.

Thanks anway!


perixx

---

### Post by perixx on 2007-10-28
Allright, I got it done!


Now I did the following, analog to the information on OO-forums - I completely removed the old OO version with Synaptic, closed it again and then:

1) downloaded the localized archive, linked on suggested site
[http://download.openoffice.org/index.html](http://download.openoffice.org/index.html)

2) used Xarchive to unpack it to the new directory /home/USER/tmp

3) opened a Terminal in that directory and typed
sudo dpkg -i *.deb

Finished - Thanks for help!


perixx

---

### Post by perixx on 2007-10-31
Update:

My problem with the freezing Impress application of OpenOffice (and many other) seems to be definitely a bug, originating from faulty Ubuntu repository packages. 

Many problems with OO's current Ubuntu-version from the official repos have been reported in the OpenOffice forums!
See this link for reference:

> [http://www.oooforum.org/forum/viewtopic.phtml?t=64806&sid=510cd8f3144c057d6d7d89714d8e6b27](http://www.oooforum.org/forum/viewtopic.phtml?t=64806&sid=510cd8f3144c057d6d7d89714d8e6b27)

My recently found 'fix' by replacing Ubuntu's OO with the newest official Debian version could possibly also solve many other problems - 

MAYBE IT'S BEST NOT TO USE UBUNTU-OPENOFFICE AT ALL...! 


perixx

---

