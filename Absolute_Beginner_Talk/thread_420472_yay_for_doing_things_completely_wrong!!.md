---
title: "yay for doing things completely wrong!!"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by unluckystarman on 2007-04-23
background: i set up ubuntu in a dual boot with windows xp and in that process, accidentally formatted one my drives and lost 200 gigs of music, movies, and work. whoops...i'll assume i messed up in the partitioning stage of installing ubuntu. it really sucks...i'm pissed at myself at losing a lot of personal work with regards to the recordings i had done (i'm a musician/sound engineer) but in general....not much i can do at this point.


but now....i'm quite lost. i was trying to get my screen res up to the proper resolution and when i went to restart the system (by using the terminal) i now get a dos-like prompt whenever i start ubuntu and i'd like to get back to an actual GUI usage rather than prompts. i tried searching in the history but can't seem to find what i've done...not to mention in how i messed up is probably idiotically unique.



things i did to mess my ubuntu (feisty fawn):

first thing i did was try installing a new software...the glx new for nvidia which uninstalled the current nvidia. i'm guessing this is most likely where things went wrong.

anyways, after i did that, i went into the terminal and tried

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

as suggested by another guide.

then used the command sudo /etc/init.d/gdm restart   to restart my system.

after that i got the black screen of "i'm way too amature to get this done."  and i'd love to get back to having an actual gui on bootup rather than a black prompt screen.

then after that...maybe someone could tell me how to set up my driver to display 1600x1200....which is what i was trying to do in the beginning anyways (the screen resolutoin thing only had up to 1076x768 res with a refresh of 60).

....at least i remembered all my steps in how i messed up. *shrugs*

---

### Post by sunexplodes on 2007-04-23
Getting a GUI is easy, from that point. 

type in: nano /etc/X11/xorg.conf

and look for this: 
```
Section "Device"
	Identifier	"nVidia Corporation [YOUR CARD MODEL]"
	Driver		"nvidia"
```

And change it to:

```
Section "Device"
	Identifier	"nVidia Corporation [YOUR CARD MODEL]"
	Driver		"nv"
```


Reboot, and you're in again.

---

### Post by Kingsley on 2007-04-23
You probably should've tried
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by unluckystarman on 2007-04-23
thanks..i'm gonna try that right now...hopefully my next post will be from ubuntu.

---

### Post by unluckystarman on 2007-04-23
nope...x-server failed...no boot screen?

---

### Post by unluckystarman on 2007-04-23
i'd really like to be able to get back on ubuntu....*bump statement*

---

