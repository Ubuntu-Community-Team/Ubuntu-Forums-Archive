---
title: "[SOLVED] Nebie WINE question"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by azalamo99 on 2008-01-13
Ok, I have gotten WINE installed and the application I want to run on it sort of works. My question is about the size of the WINE desktop screen. It sits in the middle of my laptop screen and is about one third of the screen size. I have not been able to figure out how to expand the WINE desktop screen to "full size". Can someone tell me if this is possible and point me to the right procedure? Thanks.
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by djbsteart1 on 2008-01-13
if you go to wine in the start menu, then to the configure tab it should be possible to set this up there

---

### Post by azalamo99 on 2008-01-14
Well you see that is part of the problem. The "Configure Wine" opens the WNE window which is too small to see all the options. There is no scroll bar and I can't move the window up high enough to see the bottom of the window. I can barely see a screen resolution slider bar but moving it doesn't help. I can't still find (or see) anyway to apply any changes and the original screen size stays the same. That seems to still be my problem.... any other method to change this resolution???

---

### Post by fiddledd on 2008-01-14
See if this helps:

[http://wiki.jswindle.com/index.php/Wine_Config_File](http://wiki.jswindle.com/index.php/Wine_Config_File)

You can edit the wine config file in gedit.

EDIT:
Your specific problem isn't covered there, but I'm thinking you can change the resolution etc, it won't be hard to spot.

---

### Post by fiddledd on 2008-01-14
Sorry, ignore my last post, it won't work, the config file isn't there anymore. You could only do it if typing "regedit" in the terminal brings up regedit with a big enough window, and I'm guessing it won't.

---

