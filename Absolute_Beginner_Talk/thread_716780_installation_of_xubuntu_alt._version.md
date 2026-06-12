---
title: "installation of xubuntu alt. version"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by stigpetter on 2008-03-06
trying to install xubuntu alternative version on my laptop.
(All other versions have stopped/crashed during inst)
Looks like the installation is complete but it is not 
possible to see anything on the screen. pressing
Ctrl-Alt-F7 to F9 only give a frozen image of the desktop that turns whiter & whiter until screen is white. 
Installed MS-xp to check if there was hardware problems-XP came up very nice.
I assume comp problem with screen or controllercard in xubuntu?
All help welcome

---

### Post by kellemes on 2008-03-06
Have you tried the following to at least get some desktop?
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by stigpetter on 2008-03-06
Thx but it did not work.
Have tried all possible solutions in the modifyer, but no.
It is a FSC-S6010 laptop with intel 830MG chipset.
Internal flat panel w 1024x768 - 24bit.

---

### Post by kellemes on 2008-03-06
Don't give up on "sudo dpkg-reconfigure xserver-xorg" too easy.. ;-)

I don't have an easy fix for your issue but the following poster has the same chipset and got it working, maybe you should try this..
[http://ubuntuforums.org/showthread.php?t=624032&highlight=830MG]("http://ubuntuforums.org/showthread.php?t=624032&highlight=830MG")

This poster has the same chipset..
[http://ubuntuforums.org/showpost.php?p=3890806&postcount=15]("http://ubuntuforums.org/showpost.php?p=3890806&postcount=15")

It seems you need to select i810 driver at least.

Good luck.

---

### Post by stigpetter on 2008-03-06
Thank you very much.
Purr like a kitten.:popcorn:

---

