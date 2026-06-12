---
title: "gnome-terminal to start rather than xterm"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Glenn Jones on 2007-07-17
Hey guys 

First off apologies but I had no idea where to post this. I've got ubuntu installed on my desktop at home and have an apple macbook for. I am basically trying to configure my macbook to be as similar to my desktop as possible hence my adoption of x11 and a load of other open source software. My question is a general terminal configuration thing. I recently downloaded the gnome-terminal  (path /sw/bin/gnome-terminal) and I'm wondering how to get it to start rather than the xterm. I assume I must modify my .Xdefaults file but I have no idea where to start.

Below is a copy of my .Xdefaults file

*customization: -color
XTerm*VT100.Translations: #override\
        <Key>Prior: scroll-back(1,page)\n\
        <Key>Next: scroll-forw(1,page)\n\
        <Key>Home: scroll-back(1000,page)
*XTerm*deleteIsDEL: true
xterm*saveLines: 10000
xterm*scrollBar: true
xterm*rightScrollBar: true
xterm*jumpScroll: true
xterm*faceName: Monaco 
xterm*faceSize: 11
xterm*visualBell: true
xterm*charClass: 43:48,45-47:48,95:48,127:48


Cheers

Glenn

---

### Post by jpietari on 2007-07-29
I'm assuming that you are using gnome (not kde).

Try change the setting in "Preferred Applications".  Depending on your main menu structure, you can navigate to it by clicking System->Preferences->Preferred Applications then clicking the "System" tab.

Hopefully this helps.

---

