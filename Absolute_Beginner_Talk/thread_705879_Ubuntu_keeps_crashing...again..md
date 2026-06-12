---
title: "Ubuntu keeps crashing...again."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by hottshot104 on 2008-02-23
Hey everyone.

This is my second fresh install of ubuntu today.

I installed ubuntu earlier, and while trying to figure out how to make the title bar font and the login screen fonts return to normal, I stumbled upon this forum topic:

[http://ubuntuforums.org/showthread.php?t=583915&highlight=title+bar+huge&page=2](http://ubuntuforums.org/showthread.php?t=583915&highlight=title+bar+huge&page=2)

and followed this procedure:

This only fixed the problem until I restarted, at which point it returned. I have managed to fix it permanently however. This is what I did:
1. sudo gedit /etc/gdm/gdm.conf
2. find the section [server-Standard] in that file
3. You should see a line that says "-command=/usr/bin/X -br -audit 0". Change it to read "-command=/usr/bin/X -br -audit 0 -dpi 96".
4. Save, quit, and restart

Upon restart, I now cannot login to Ubuntu. 

The computer starts up, and then the ubuntu loading screen distorts and a message stating that ubuntu cannot recognize my video card appears. Regardless of whether I choose to continue using low graphics setting, the computer will reset back to the "ubuntu cannot recognize video card" screen and repeat the same thing.

Please help me fix this as I really do not want to do ANOTHER install of ubuntu, all within less than six hours' time.

---

### Post by Crafty Kisses on 2008-02-23
What kind of Video Card do you have?

---

### Post by hottshot104 on 2008-02-23
It is an Intel integrated graphics card. 945 series I believe.

Either way, the advice provided in that thread screwed up my ubuntu OS, again, and I hope that someone can please help me out.

---

### Post by hottshot104 on 2008-02-23
*bump*

Someone please help me I don't want to reinstall.

Is there any way to recover gmd.conf?

---

### Post by hottshot104 on 2008-02-23
*bump*

---

### Post by hottshot104 on 2008-02-23
...Maybe I should just reformat again...or go back to windows.

---

### Post by Iceni on 2008-02-23
Hey man, why don't you try the following things before reinstalling:

1. Undo your edits to the gdm.conf file. It was the last thing you did before it broke, so it makes sense to undo it to see if that is the problem.

2. Alternative:

Open a console: ctlr+alt+f1
login

```
sudo nano /etc/X11/xorg.conf
```

Scroll down till you find your video card. Mine looks like this:

> Section "Device"
	Identifier	"nVidia Corporation NV41 [GeForce 6800 GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Change the driver value to "vesa". Save and exit nano. Now go back to your x console:

ctlr+alt+f7.

restart x:
ctlr+alt+backspace

try to log in.

---

