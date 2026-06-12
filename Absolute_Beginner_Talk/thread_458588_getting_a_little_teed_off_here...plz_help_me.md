---
title: "getting a little teed off here...plz help me"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by bishop9226 on 2007-05-29
I installed wine on ubuntu via automatix and then uninstalled it and did it again with synaptic.  same result.  everyone else gets to install it and then click on exe's and have it work, yet when *I* install it, IT ACTS LIKE IT ISNT EVEN THERE! I CLICK ON A SIMPLE EXE, UTORRENT.EXE for example, and i get >  No application suitable for automatic installation is available for handling this kind of file.

so even though i installed wine, it isnt even acting like its installed on my computer.  another guy said as soon as he installed it it was in the apps menu, and another guy said he could just right click on exe files and do "open with" then select "wine", yet when *I* install it, i get none of this.  I want to get photoshop cs2 working but opening a simple exe file with wine should come first.

What the heck is going on

---

### Post by Hobo Joe on 2007-05-29
Click 'open with' then select WINE.

---

### Post by bishop9226 on 2007-05-29
Im Telling You That When I Click "open With" Wine Isnt There!!!!!

---

### Post by Peetke on 2007-05-30
Can you type "wine" at the "open with" prompt?

---

### Post by meborc on 2007-05-30
you should do the configuretion of wine, if you have not done so earlier - just type "winecfg" in the terminal... now it should be ready to run...

---

### Post by sankarv on 2007-05-30
you have to do only that as peetke said since wine is not listed in the default open applications. you can enter the custom command to open with as wine for the exe files and thereafter they are automatically opened with the command.


in commandline  u can type



> wine <filename with path>.exe



that also will work....

---

