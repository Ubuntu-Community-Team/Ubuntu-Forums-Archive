---
title: "Graphics problem"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Medzi on 2007-08-30
Hi I am a complete newbie in the Ubuntu area and I am in need of help!
I dont think my graphics card drivers are installed firstly when I try to install them it gives me errors

Another problem I am having is that I installed some games and everytime I try to play them they blink for a moment then close right away

Any Help is appreciated Thanks!

if it Helps I have a Nvidia 7600 GT

---

### Post by ericmitz on 2007-08-30
What kind of symptoms make you think your graphics card is not working properly? is it just the flickering?

type:
```
glxinfo | grep rendering
```

you should see:

```
direct rendering: Yes
```

---

### Post by Medzi on 2007-08-30
When I try that this is what I receive:

glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by Clay_Banger on 2007-08-30
i cant remember where, but under one of the administration menus there will be a thing called "Restricted Drivers Manager" or something similar. Fire that up and it will download/install the correct drivers for your video card.

---

### Post by Medzi on 2007-08-30
I looked but I did not see anything that said restricted drivers manager

---

### Post by Clay_Banger on 2007-08-30
> **Medzi said:**
> I looked but I did not see anything that said restricted drivers manager

sorry about being a bit vague before.

System > Administration > Restricted Drivers Manager

[IMG]http://www.michaellarabel.com/external/restricted-0.jpg[/IMG]

---

### Post by Medzi on 2007-08-30
Wierd but I dont have that under my Administration menu:confused:

---

### Post by Clay_Banger on 2007-08-30
> **Medzi said:**
> Wierd but I dont have that under my Administration menu:confused:

what version of ubuntu are you using? the restricted drivers manager is a fairly new thing.

---

### Post by Medzi on 2007-08-30
6.10 Edgy

---

### Post by Clay_Banger on 2007-08-30
ok, it must only be in 7.04 then.. anyway, this will install the correct drivers for you(well i use them and i have a 7600gs):

open up the terminal:
```
sudo aptitude install nvidia-glx-new
```
then reboot and they should be installed.

---

### Post by Medzi on 2007-08-30
I tried that and this shows up

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "nvidia-glx-new"
The following packages have been kept back:
  k3b libk3b2 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


So nothing really happened

---

### Post by Clay_Banger on 2007-08-30
it didnt work because you havent enabled the extra repos.

go here [http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources") and follow the instructions for 6.10, then do:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install nvidia-glx-new
```
and reboot.

---

### Post by Medzi on 2007-08-30
I did that and I still get the same as before

Btw thanks for the help so far

---

### Post by Clay_Banger on 2007-08-30
> **Medzi said:**
> I did that and I still get the same as before

Btw thanks for the help so far

:confused: what about:
```
sudo aptitude install nvidia-glx
```

---

