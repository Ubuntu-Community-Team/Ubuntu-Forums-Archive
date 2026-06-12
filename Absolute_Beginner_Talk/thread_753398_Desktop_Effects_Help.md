---
title: "Desktop Effects Help"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by R6V2 on 2008-04-12
My desktop effects no longer work, I get the problem:

jkg-jockey (or something) when tring to set my desktop effects

Why is this happening?

---

### Post by Tomatz on 2008-04-12
Run this in a terminal and post the output:

compiz --replace

---

### Post by R6V2 on 2008-04-12
darin@Darin:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by Inxsible on 2008-04-12
> **R6V2 said:**
> darin@Darin:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacityInstall xgl by ```
 sudo aptitude install xserver-xgl
```Try to enable compiz after installing it and see if that works

---

### Post by Tomatz on 2008-04-12
> **R6V2 said:**
> darin@Darin:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity


It is basically saying that it (compiz) doesn't support your graphics drivers/GPU.

Have you updated your drivers recently?

---

### Post by Tomatz on 2008-04-12
> **Inxsible said:**
> Install xgl by ```
 sudo aptitude install xserver-xgl
```Try to enable compiz after installing it and see if that works

Don't install xgl thats just mad.

---

### Post by R6V2 on 2008-04-12
I just updated my drivers yesterday.

---

### Post by R6V2 on 2008-04-12
I installed it, and how do I enable compiz?

---

### Post by Inxsible on 2008-04-12
> **Tomatz said:**
> Don't install xgl thats just mad.Care to explain why ? I don't need xgl on my graphics card, but I figure I should know in case I come across a similar problem.

---

### Post by Inxsible on 2008-04-12
> **R6V2 said:**
> I installed it, and how do I enable compiz?
Open up a terminal and type in```
compiz -- replace
```

Or you can go to System>>Preferences>>Appearance. On the visual effects tab, select Extra or Custom. You may have to restart X, i think

---

### Post by Tomatz on 2008-04-12
> **R6V2 said:**
> I just updated my drivers yesterday.

This is why. Your drivers are blacklisted you need to disable hardware checks.

Xgl wont solve the problem it will just be a slow, buggy workaround :(

---

### Post by Tomatz on 2008-04-12
Type this in a terminal then restart compiz:


echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager


It should work then ;)

---

### Post by R6V2 on 2008-04-12
The compiz -- replace says the same as last time..

---

### Post by Inxsible on 2008-04-12
> **R6V2 said:**
> The compiz -- replace says the same as last time..The --replace is without a space between them

---

### Post by Tomatz on 2008-04-12
> **R6V2 said:**
> The compiz -- replace says the same as last time..

Do this:

echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

Trust me xgl wont help at all.

---

### Post by R6V2 on 2008-04-12
I typed that  echo thing, and then typed the compiz thing, and still cant enable my desktop effects, same as start.

---

### Post by Tomatz on 2008-04-12
> **R6V2 said:**
> darin@Darin:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
[beer]

---

### Post by Tomatz on 2008-04-12
> **R6V2 said:**
> I typed that  echo thing, and then typed the compiz thing, and still cant enable my desktop effects, same as start.

remove xgl then reboot.

sudo apt-get remove xserver-xgl

---

### Post by Tomatz on 2008-04-12
> **Inxsible said:**
> The --replace is without a space between them

This is true ;)

---

### Post by R6V2 on 2008-04-12
Ok...I remove xserver-xgl, and still no desktop effects working...

---

### Post by Crafty Kisses on 2008-04-12
I'm not sure if this has been suggested but can you post the following output:
```
glxinfo
```

---

### Post by Tomatz on 2008-04-12
> **R6V2 said:**
> Ok...I remove xserver-xgl, and still no desktop effects working...

And you rebooted/logged out?

---

### Post by R6V2 on 2008-04-12
This problem still stumps everyone?

---

### Post by R6V2 on 2008-04-12
> **Codename said:**
> I'm not sure if this has been suggested but can you post the following output:
```
glxinfo
```
darin@Darin:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
darin@Darin:~$ 



And, yes I've rebooted 4 times.

---

### Post by Tomatz on 2008-04-12
The problem is that compiz doesn't support the drivers you have installed. They are **balcklisted**.

E.g:

*No whitelisted driver found*

The "echo" command i told you to do should have overridden the "blacklist".

May i ask **how, why and where** you got the drivers?

---

### Post by R6V2 on 2008-04-12
Well Nvidia doesn't support my driver so I got it from here

[http://www.driverfiles.net/Video-Adapters/nVIDIA/GeForce3-Ti-200/download/page,sh,23291,459,5,.html](http://www.driverfiles.net/Video-Adapters/nVIDIA/GeForce3-Ti-200/download/page,sh,23291,459,5,.html)

So...

I use a nvidiai GeForce3 ti 200

---

### Post by Tomatz on 2008-04-12
> **R6V2 said:**
> darin@Darin:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
darin@Darin:~$ 



And, yes I've rebooted 4 times.


Ahhh

Add this to the "**screen**" section of your xorg.conf file:

**Option		"AddARGBGLXVisuals"	"True"**

To do this:

**sudo gedit /etc/X11/xorg.conf**

Add it

Then save and logout

;)

---

### Post by Tomatz on 2008-04-12
> **R6V2 said:**
> Well Nvidia doesn't support my driver so I got it from here

[http://www.driverfiles.net/Video-Adapters/nVIDIA/GeForce3-Ti-200/download/page,sh,23291,459,5,.html](http://www.driverfiles.net/Video-Adapters/nVIDIA/GeForce3-Ti-200/download/page,sh,23291,459,5,.html)

So...

I use a nvidiai GeForce3 ti 200

And you can run compiz on a geforce 3?

Thats crazy if you can. I didn't think it was possible :confused:

---

### Post by Tomatz on 2008-04-12
Why didn't you use the nvidia-legacy packaged drivers?

---

### Post by R6V2 on 2008-04-12
I don't know...I just want my desktop effects. :( . They worked completely fine on 7.10.

---

### Post by R6V2 on 2008-04-12
> **Tomatz said:**
> Ahhh

Add this to the "**screen**" section of your xorg.conf file:

**Option		"AddARGBGLXVisuals"	"True"**

To do this:

**sudo gedit /etc/X11/xorg.conf**

Add it

Then save and logout

;)
Still doesn't work...

---

### Post by overdrank on 2008-04-12
> **R6V2 said:**
> I don't know...I just want my desktop effects. :( . They worked completely fine on 7.10.

And are you still using 7.10?

---

### Post by Tomatz on 2008-04-12
> **R6V2 said:**
> I don't know...I just want my desktop effects. :( . They worked completely fine on 7.10.

Your card is blacklisted from compiz mate :(

Basically the compiz devs probably think your card and/or drivers are out of date. So they aren't supporting it/them.

You could always try the nvidia-legacy drivers:

**sudo apt-get install nvidia-glx-legacy**

then

**sudo nvidia-glx-config enable**

There is a **good chance** it could **bork**. If it does, login (at the terminal) and type this at the terminal/command prompt:

sudo dpkg-reconfigure -phigh xserver-xorg

*It would probably be a good idea if you write this^ down (no typos)*

:)

---

### Post by R6V2 on 2008-04-12
darin@Darin:~$ sudo nvidia-glx-config enable
sudo: nvidia-glx-config: command not found
darin@Darin:~$ 

In other words...it didnt work.

---

### Post by Tomatz on 2008-04-12
Strange?

Did you install the driver with the first command (sudo apt-get install nvidia-glx-legacy)? If not then you need to do so before doing the "config-enable" command.

This is the description of the "legacy" drivers:
> 
[I]NVIDIA binary XFree86 4.x/X.Org 'legacy' driver
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and supports the TNT,
TNT2, TNT Ultra, GeForce, and GeForce2 chipsets. AGP, TV-out and flat panel
displays are also supported.

This is the 'legacy' driver for older chipsets.  Unless your chipset is
explicitly listed in the above paragraph, please use the nvidia-glx driver,
which is much more up to date.

To enable the driver, run "sudo nvidia-glx-config enable".[/I]

As you can see the "config-enable" command is at the bottom.

Give your computer a reboot but make sure you write down:

**sudo dpkg-reconfigure -phigh xserver-xorg**

As you will probably need it.

---

### Post by R6V2 on 2008-04-12
Yep, I did the actual install command first, then that, it said it didn't exist...........

---

### Post by Tomatz on 2008-04-12
Try a reboot but as i keep saying, have this to hand:

**sudo dpkg-reconfigure -phigh xserver-xorg**

I'm off now its nearly 1200 pm here. Ill check back first thing tomorow :)

Hope you have some luck though.

---

### Post by R6V2 on 2008-04-12
Thanks.

---

### Post by R6V2 on 2008-04-12
I apperciate everyones help here! But does anyone else have a different approach? :)

---

### Post by overdrank on 2008-04-12
> **R6V2 said:**
> I apperciate everyones help here! But does anyone else have a different approach? :)

HI and you are using a nvidiai GeForce3 ti 200 graphics card and are you still using Hardy? Could you post the output of ```
cat /etc/X11/xorg.conf
``` If you are using Hardy, then what driver were you using in gusty 7.10?

---

