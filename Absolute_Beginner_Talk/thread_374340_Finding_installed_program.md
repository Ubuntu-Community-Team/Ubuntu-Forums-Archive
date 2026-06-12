---
title: "Finding installed program"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-03-02
I installed gqcam using Synaptic to see if my Creative webcam will work in Ubuntu. It seemed to install OK, and Synaptic shows it as installed. I couldn't find it on the menus, or in Alacarte menu editor, so I entered "gqcam" at the terminal, which gives the error message "/dev/video: No such file or directory".

So is it installed, and if so, how can I find it?

TIA

---

### Post by Maestro23 on 2007-03-02
In terminal try:

> whereis

which

locate

*Is the camera plugged in when you try to execute the program?

---

### Post by freesitebuilder on 2007-03-02
whereis gives me
gqcam: /usr/bin/gqcam /usr/bin/X11/gqcam /usr/share/man/man1/gqcam.1.gz

---

### Post by Maestro23 on 2007-03-02
> **freesitebuilder said:**
> whereis gives me
gqcam: [COLOR="Red"]/usr/bin/gqcam[/COLOR] /usr/bin/X11/gqcam /usr/share/man/man1/gqcam.1.gz

That is the path to the .bin(executable).

---

### Post by Nythain on 2007-03-02
not familiar with this app butsince it didnt return
bash: gqcam: command not found
it looks like its installed, just needs some configuration... its looking somewhere where that doesnt exist for whatever its trying to do... i would head to the homepage of the app and look for any setup instructions after installing... this is linux, there's bound to be a conf file for it somewhere...

---

### Post by Maestro23 on 2007-03-02
> **Nythain said:**
> not familiar with this app butsince it didnt return
bash: gqcam: command not found
it looks like its installed, just needs some configuration... its looking somewhere where that doesnt exist for whatever its trying to do... i would head to the homepage of the app and look for any setup instructions after installing... this is linux, there's bound to be a conf file for it somewhere...

Beat me to it Nythain.:)

---

