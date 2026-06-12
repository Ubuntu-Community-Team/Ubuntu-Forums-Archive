---
title: "problem with gdesklets"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by wasp on 2006-04-10
I have a noobish problem here, I'm sure.

I decided to try gdesklets, and get the tuxclocks and starterbar and stuff like that. So I install gdesklets, and when I go applications > accessories > gdesklets, it seems to try to load and then stops. I have tried this several times, and it doesn't work. I'm also not sure where to put the things I've downloaded for gdesklets. I have the tuxclocks and starterbar like I said, but they are tarred, and I don't know what directory to put them in. If anyone could help with this, it would be appreciated. :) 

P.S. P.S. I'm not sure if the "g" in gdesklets stands for Gnome. Do you have to be in Gnome for it to work? I'm using Xubuntu.

---

### Post by mstlyevil on 2006-04-10
[QUOTE=wasp]I have a noobish problem here, I'm sure.

I decided to try gdesklets, and get the tuxclocks and starterbar and stuff like that. So I install gdesklets, and when I go applications > accessories > gdesklets, it seems to try to load and then stops. I have tried this several times, and it doesn't work. I'm also not sure where to put the things I've downloaded for gdesklets. I have the tuxclocks and starterbar like I said, but they are tarred, and I don't know what directory to put them in. If anyone could help with this, it would be appreciated. :) 

P.S. I'm not sure if the "g" in gdesklets stands for Gnome. Do you have to be in Gnome for it to work? I'm using Xubuntu.[/QUOTE]

For tux clocks and the starter bar, just go to synaptic and install gdesklets data. Then you will have most desklets already installed.

To start gdesklets in xubuntu, open a terminal and type 

```
gdesklets
```

into it and see if they start. Yes the g in gdesklets do stand for gnome, but I have had them working in Xubuntu also.

---

### Post by wasp on 2006-04-10
[QUOTE=mstlyevil]For tux clocks and the starter bar, just go to synaptic and install gdesklets data. Then you will have most desklets already installed.

To start gdesklets in xubuntu, open a terminal and type 

```
gdesklets
```

into it and see if they start. Yes the g in gdesklets do stand for gnome, but I have had them working in Xubuntu also.[/QUOTE]

Great, it's working!

I don't know why it wouldn't work from the menu, but it worked from the terminal. 

Thanks a lot. :D

---

### Post by mstlyevil on 2006-04-10
[QUOTE=wasp]Great, it's working!

I don't know why it wouldn't work from the menu, but it worked from the terminal. 

Thanks a lot. :D[/QUOTE]

No problem, was glad to help.

---

### Post by jcranwellward on 2006-07-17
I have installed gdesklets and starterbar package, but when i double click i get the following error

Traceback (most recent call last):
  File "/usr/lib/gdesklets/factory/SensorFactory.py", line 42, in create_sensor
    os.chdir(p)
OSError: [Errno 2] No such file or directory: '/usr/lib/gdesklets/../../share/gdesklets/Sensors'

Im running Gnome on debian so you might not want to help, but im really stuck and would be gratefull for the help.

---

