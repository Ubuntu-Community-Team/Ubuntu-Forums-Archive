---
title: "wine etc?Games in window?HOW?software or opengl when doing this?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-03-30
hi people, how do i run my wine games for example cs1.6 in a window as if their a normal app?
i'd REALLY like to do this! I've seen it in pictures with cedega and i don't know if its specific to that or if it's possible with wine? is it only software rendering or can i do it with opengl? i mean surely its possible seeing as i can mupen64 runs in opengl and thats windowed... so must be possible right?


so what i want to know is how do i run games (mainly on about wine games here) in a window in opengl?
cheers

---

### Post by david_kt on 2007-03-30
May be you could take alook at this web:

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS)

but I never try it yet though, as I don't play games.

DK

---

### Post by zvacet on 2007-03-31
You can run games in wine and in cedega.Wine is free and Cedega is commercial.Cedega is made for games but that doesn´t mean that you can not run games in wine.

---

### Post by keef247 on 2007-03-31
think your all a little comfused.i know how to use wine im just asking how do i play the games in a window as you would when you run a application. and will running games in wine etc make it render in software mode instead of opengl?
cheers
sorted it.chose to run winecfg and then select a virtual desktop and specified a resolution etc etc...

---

### Post by ikonia on 2007-04-01
there is a wine wiki page on the ubuntu wiki that talks through both installing and running wine and windows applications from within wine

---

### Post by kahrytan on 2007-04-01
Assuming you got Wine installed
 If you want to run a application in Window mode. 

1. Press ALT-F2 or open a Terminal window. 
2. type Wincfg. 
3.  Under the graphics tab, You will see Emulate a virtual desktop. Check the box and choose your desktop size.  For example, 800x600 or 1074x768.  Set it below your current desktop resolution.
4. Then click OK.
 
For now on, every wine application will run in that virtual desktop space.

EDIT: 

Wine attempts to do Hardware based Direct3D and DirectSound.

---

### Post by Maestro23 on 2007-04-01
> **ikonia said:**
> there is a wine wiki page on the ubuntu wiki that talks through both installing and running wine and windows applications from within wine

Maybe these:

Wine: [https://help.ubuntu.com/community/Wine?highlight=%28Wine%29](https://help.ubuntu.com/community/Wine?highlight=%28Wine%29)

Games in Wine: [https://help.ubuntu.com/community/Games](https://help.ubuntu.com/community/Games)

---

### Post by ikonia on 2007-04-01
correct, very easy for keef247 to find for himself and read.

---

