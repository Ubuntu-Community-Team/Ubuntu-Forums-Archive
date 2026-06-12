---
title: "I Know alot but not enough"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by RikJr on 2007-02-08
I need help with 3 things that im having problems with

1. installing nvidia drivers
2.installing a program called WINE
3.i cant locate the Theme folder

---

### Post by igknighted on 2007-02-08
> **RikJr said:**
> I need help with 3 things that im having problems with

1. installing nvidia drivers
2.installing a program called WINE
3.i cant locate the Theme folder

1. ```
sudo aptitude install nvidia-glx
```

2. Try ```
sudo apt-cache search wine
``` and see if that turns anything up.  I know automatix2 can automate part of the install for you as well if you want to mess with that.  I think your best bet is to go to [www.winehq.com](www.winehq.com) for more info, and package downloads.

3. it is in you home folder (/home/username), and it is called ".themes".  This is important because in linux any folder that starts with "." is hidden, so you need to hit <ctrl> + <h> to show it.

---

### Post by jd65pl on 2007-02-08
1.  Nvidia [http://doc.gwos.org/index.php/Install_Nvidia_driver](http://doc.gwos.org/index.php/Install_Nvidia_driver)

---

### Post by Repent on 2007-02-08
I used this program to install the nVIDIA drivers for my card and it worked great.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by RikJr on 2007-02-08
> **igknighted said:**
> 1. ```
sudo aptitude install nvidia-glx
```

2. Try ```
sudo apt-cache search wine
``` and see if that turns anything up.  I know automatix2 can automate part of the install for you as well if you want to mess with that.  I think your best bet is to go to [www.winehq.com](www.winehq.com) for more info, and package downloads.

3. it is in you home folder (/home/username), and it is called ".themes".  This is important because in linux any folder that starts with "." is hidden, so you need to hit <ctrl> + <h> to show it.

THANK YOU!

---

### Post by RikJr on 2007-02-08
Ok i did that now how do i USE WINE ? and now is the nivida drivers are install i typed in that code like u said in the terminal  and it did its thing... is it installed now? and i did the same thing for wine is that installed?

---

### Post by lyceum on 2007-02-08
winecfg 

in terminal to set it up.

---

### Post by RikJr on 2007-02-08
i set it up how do i run it now?

---

### Post by lyceum on 2007-02-08
well, I use Crossover myself, but..heres a link

[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

hope it helps

---

### Post by igknighted on 2007-02-08
for the NVIDIA drivers, to test if your system is indeed using them, log out of ubuntu then log back in.  If you get an NVIDIA splash screen then it loaded fine, otherwise you will have to update your xorg.conf file to tell X what driver to use.

---

### Post by RikJr on 2007-02-08
no i do not get a splash screen with nvidia ... hoe do i update that config file you were talking about....YES I NO IM A COMPLETE NEWB i only used windows all my life so ya :P

---

### Post by jd65pl on 2007-02-08
I don't get an nvidia splash and I am definately using the drivers. do the command below return 'yes'
```
glxinfo | grep direct
```

---

### Post by RikJr on 2007-02-08
i typed that in and nothing happened

im using a nvidia 7600 gs does that change anything?

---

### Post by RikJr on 2007-02-08
this is wat i get when i type in that code

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

### Post by muguwmp67 on 2007-02-08
If you installed the drivers through synaptic, you need to type:

```
sudo nvidia-glx-config enable
```

to finish the install.

---

### Post by RikJr on 2007-02-08
i didnt install through synaphitc

---

### Post by RikJr on 2007-02-08
anyone?

---

### Post by RikJr on 2007-02-08
this is wat i get wen i type in sudo nvidia-glx-config enable


rik@Gaming:~$ sudo nvidia-glx-config enable
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.
rik@Gaming:~$

---

### Post by Repent on 2007-02-08
Would you just please try Envy?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by RikJr on 2007-02-08
how do i install envy

---

### Post by RikJr on 2007-02-08
does anyone no?

---

### Post by RikJr on 2007-02-08
Envy??? how do you install it?

---

### Post by RikJr on 2007-02-08
no ?

---

### Post by Repent on 2007-02-08
Click on the link  [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb)  to download . Then open a terminal and type envy.

P.S. use the GDebi Package install it for you.

---

