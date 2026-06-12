---
title: "please helap, i cant run mercury msn :S"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Javs on 2008-04-17
ive just installed mercury msn, but when i click on sing in, nothing happen!!! anyone can help me please¡?

---

### Post by spiderbatdad on 2008-04-17
You still have to have a .net passport and input the information in mercury messenger somewhere...sorry for lack of directions...been a couple of years since I have used mm.

---

### Post by Javs on 2008-04-17
im new with ubuntu, so i dont know much, i needed a msn with video call, is there another that is beter than this? and also i think i have to instal webcam and audio software for the msn, but i dont know wich is it.

---

### Post by spiderbatdad on 2008-04-17
kopete has video support...not 100% sure it supports msn...but I would guess it does.
```
sudo apt-get install kopete
``` look for it under Applications>>Internet...You may need to add an additional package for the video. I can't remember, but the program will inform you when you try to use video mode. To use msn, you have to have a .net passport...it's a microsoft thing.

---

### Post by racoq on 2008-04-17
Try aMSN ([http://amsn.sourceforge.net](http://amsn.sourceforge.net)) it is in the repository's and it does fully support Webcams for MSN

```

sudo apt-get install amsn

```

---

### Post by ~L~ on 2008-04-18
i installed mercury but cant find it under internet or any applications

---

### Post by SunnyRabbiera on 2008-04-18
> **~L~ said:**
> i installed mercury but cant find it under internet or any applications

It doesnt look like it adds a shortcut to the menu's, dont worry I have a remedy:
right click on your menu and select "edit menus"
mosey down to internet and click on "new item"
after this a new window will become available in the bottom panel (taskbar) labeled create launcher
just click on it and bring it up.
Put for the name Mercury messenger and then click on the button "browse" next to the box that is labeled "command"
now find your way to usr/bin by first clicking on "file system"
then to usr
then to bin
then mosey down to the executable "mercury"
click open
and you are practically done!
now click the box with the little spring thingie in it to make an icon for it
a little window will pop up and click on "browse"
make your way to the "crystalsvg" folder
then to 48x48
then to apps
click open and select the Mercury icon
click "ok"
then again "ok"
and boom you got a launcher for Mercury!

---

### Post by Peter Great on 2008-04-20
Mercury didn't work until I installed Sun Java 6 from Synaptic. It does not work under GNU Java.

---

