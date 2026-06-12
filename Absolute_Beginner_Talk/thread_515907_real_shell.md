---
title: "real shell"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by deadfred_10 on 2007-08-02
I need to get a real shell, not a terminal. I need to install the real Nvidia driver and I can't do that through konsole,

---

### Post by annda on 2007-08-02
> **deadfred_10 said:**
> I need to get a real shell, not a terminal. I need to install the real Nvidia driver and I can't do that through konsole,

are you using sudo? what seems to be the problem?

---

### Post by apswartz on 2007-08-02
Try Ctrl-Alt-F2 and login.

---

### Post by apswartz on 2007-08-02
Then Ctrl-Alt-F7 to get back to your GUI.

---

### Post by deadfred_10 on 2007-08-02
The install if the drivers require you to be in shell without any gui. In other words it would be like starting windows in dos. I tried using generic start for repair but that does not load enough stuff. There has to be a way to start a pure shell.

---

### Post by annda on 2007-08-02
you can boot into recovery mode...

---

### Post by p_quarles on 2007-08-02
There's no difference between running a shell inside KDE and running the shell from bootup. 

There is an option to load the command line on the login page. But the difficulty you're having likely lies elsewhere, and probably with the commands or syntax involved.

---

### Post by kinematic on 2007-08-02
Just go to the shel with Ctrl>Alt>F2,login and type
```
sudo killall gdm
```
in kubuntu it's
```
sudo killall kdm
```
this kills the x-server so you can install the driver.
afterwards you can start the x-server again with startx.

---

### Post by deadfred_10 on 2007-08-02
> **kinematic said:**
> Just go to the shel with Ctrl>Alt>F2,login and type
```
sudo killall gdm
```
in kubuntu it's
```
sudo killall kdm
```
this kills the x-server so you can install the driver.
afterwards you can start the x-server again with startx.

thanks for the try but that also kills the shell and you end up with a text editor. This was the reson I quit using Ubuntu because gnome was updating every couple of week and I had to install the drivers too often. Went to Mepis and got spoiled because it has  the real Nvidia drivers built in.

Now if I can only remember how I did it.

---

### Post by asmoore82 on 2007-08-02
:shock: have you tried "System -> Preferences -> Restricted Drivers" ?
and/or installing the "nvidia-glx" package via Synaptic/APT?

P.S. you should never kill gdm/kdm ... you are killing the binaries and not the script that spawns/respawns them.
Instead, stop them with
```
~ $ sudo /etc/init.d/gdm stop
```
or kdm

likewise you can start the dm again with
```
~ $ sudo /etc/init.d/gdm start
```

---

### Post by kinematic on 2007-08-07
> **deadfred_10 said:**
> thanks for the try but that also kills the shell and you end up with a text editor. This was the reson I quit using Ubuntu because gnome was updating every couple of week and I had to install the drivers too often. Went to Mepis and got spoiled because it has  the real Nvidia drivers built in.

Now if I can only remember how I did it.

no dude, that IS the shell, not a text editor.
The driver from the Nvidia site requires you to be in the shell without the x-server running.

---

