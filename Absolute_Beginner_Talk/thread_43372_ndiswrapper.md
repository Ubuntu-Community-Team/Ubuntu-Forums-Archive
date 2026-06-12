---
title: "ndiswrapper"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by next on 2005-06-21
i know there's abunch of threads on this but none of them help me.

so i was following these instructions [here](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)   but when i got to Sudo modprobe ndiswrapper it said fatal errors........operation not permitted.


i read that i have to uninstall some drivers or sumthing....i dont know



please help

---

### Post by Mr. Electric Wizard on 2005-06-21
You need the windows drivers for the device you want to install, yes.
Usually a .inf, a .sys, and/or a .cat

---

### Post by ssck on 2005-06-21
[QUOTE=next]i know there's abunch of threads on this but none of them help me.

so i was following these instructions [here](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)   but when i got to Sudo modprobe ndiswrapper it said fatal errors........operation not permitted


i read that i have to uninstall some drivers or sumthing....i dont know



please help[/QUOTE]


when you type ndiswrapper -l, what do you get ? do you see the following for your card :-

Installed ndis drivers:
neti2220        driver present, hardware present

of course, neti2220 should be the name of the card you are using

---

### Post by az on 2005-06-21
What model is it and what inf file did you use?

---

### Post by next on 2005-06-21
[QUOTE=ssck]when you type ndiswrapper -l, what do you get ? do you see the following for your card :-

Installed ndis drivers:
neti2220        driver present, hardware present

of course, neti2220 should be the name of the card you are using[/QUOTE]
 to that i get " installed drivers: autorun invalid driver"

---

### Post by next on 2005-06-21
[QUOTE=azz]What model is it and what inf file did you use?[/QUOTE]
 model of pci card? d-link dwl-g510
i used autorun.inf

---

### Post by imboden on 2005-06-21
next.

on the d-link cd, go to \Driver\manual\WinXP  and use the mrv8k51.inf file.   that is the actual INF for the card.  the autoplay.inf is just the file to activate the autoplay on a WinXX system

---

### Post by next on 2005-06-21
[QUOTE=imboden]next.

on the d-link cd, go to \Driver\manual\WinXP  and use the mrv8k51.inf file.   that is the actual INF for the card.  the autoplay.inf is just the file to activate the autoplay on a WinXX system[/QUOTE]
 thank you!! it worked

---

### Post by imboden on 2005-06-21
[QUOTE=next]thank you!! it worked[/QUOTE]
 your welcome... and its sad.... im not even on ubuntu.. the autoplay.inf line threw up a red flag for me.. thought i would post

[EDIT]

only reason i havent gotten on ubuntu is for the fact that i am only researching it for the time being

---

### Post by az on 2005-06-22
[QUOTE=imboden]next.

on the d-link cd, go to \Driver\manual\WinXP  and use the mrv8k51.inf file.   that is the actual INF for the card.  the autoplay.inf is just the file to activate the autoplay on a WinXX system[/QUOTE]



Just a note to others, the g510 has several revision (at least one) and that file may not be the correct one for some version of the card.  If the filename in that directory is different, use it anyway....

---

### Post by az on 2005-06-22
[QUOTE=imboden]your welcome... and its sad.... im not even on ubuntu.. the autoplay.inf line threw up a red flag for me.. thought i would post

[EDIT]

only reason i havent gotten on ubuntu is for the fact that i am only researching it for the time being[/QUOTE]

Welcome!

---

