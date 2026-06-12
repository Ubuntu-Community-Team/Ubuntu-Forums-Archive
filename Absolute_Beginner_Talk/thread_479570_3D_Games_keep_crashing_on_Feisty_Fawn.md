---
title: "3D Games keep crashing on Feisty Fawn"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-06-20
So far I've tried running Neverball and Egoboo (gotten from the software manager) and every time they start up, nothing happens or my monitor turns off and my PC keeps running.

Help? :(

---

### Post by steve.horsley on 2007-06-20
Have you installed 3D drivers for you video card? 
If not, what make of card do you have?

---

### Post by Kubunteando on 2007-06-20
What is your HW?
CPU, memory, graphic HW model, ...

Have installed the drivers for your Graphics card?

---

### Post by Hork on 2007-06-20
Uhhhh, 1GB of RAM, AMD Athlon, ATI Radeon 9700 Pro.

It's enough, I was able to run Half-Life 2 on max settings on Windows.


Where do I go to install drivers?

---

### Post by Tyke91 on 2007-06-20
Try the restricted drivers manager first (System>Admin>Restricted drivers) , Ubuntu doesn't come with all the drivers installed by default because of certain legal issues. I've heard that the program "ENVY" is a good way to install drivers as well.

---

### Post by Hork on 2007-06-20
I used that, and it looks like everything went okay.

The games still mess up when I start them up though. :(

---

### Post by atria on 2007-06-20
Install ati drivers with
```
sudo aptitude install xorg-driver-fglrx
```
After that open your restricted drivers manager and enable the new ATI driver that you have just installed, and reboot your computer.

When reboot completes, open your terminal again and enter
```
glxinfo | grep direct
```

and if it says yes, then the game should work.

---

### Post by Hork on 2007-06-20
Hmmm, I'm getting a yes.

In the Restrict Drivers Menu it calls it 'ATI Accelerated Graphics Card'.  I'm using a Radeon 9700 PRO.

:|

---

### Post by phr0ze on 2007-06-20
> **Hork said:**
> Hmmm, I'm getting a yes.

In the Restrict Drivers Menu it calls it 'ATI Accelerated Graphics Card'.  I'm using a Radeon 9700 PRO.

:|

Its a multi-card driver, hence the generic name. Please try it and let us know. Also, which 3d games are you trying to run and did you install them correctly? Finally, make sure you aren't using desktop effect or beryl while using a 3d game. 3d desktops can sometimes cause conflicts.

---

### Post by Hork on 2007-06-20
Tried it and same problem still occurs.

I'm trying Egoboo and Neverball.  Both installed through the Ubuntu 'Add/Remove Applications' thingie.

2D games like 'Abused' and the ones that come preloaded work just fine.

---

### Post by bobplano on 2007-06-20
whats your ```
fglrxinfo
```
if it says things like mesa then its set up wrong

---

### Post by Hork on 2007-06-20
[PHP]taylor@linuxPC:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 PRO
OpenGL version string: 2.0.6473 (8.37.6)
[/PHP]

That's exactly what happened.  Is that good?

---

### Post by Kubunteando on 2007-06-21
That looks good. Those are the latest drivers so far.

So to check deeper, can you post these two files:

- /etc/X11/xorg.conf
- /var/log/Xorg.0.log

That can give a better idea of your graphics setup.

---

### Post by whistlerspa on 2007-06-24
For me it has become simple

ATI  proprietary divers + Feisty Fawn =  screen freezes + black screens of death

ATI default drivers + Feisty Fawn = 3D games not

---

### Post by Gvaz on 2007-06-24
mine says:
> display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2


and i installed xorg from adept

:(

---

