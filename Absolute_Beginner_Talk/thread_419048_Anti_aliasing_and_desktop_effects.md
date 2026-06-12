---
title: "Anti aliasing and desktop effects?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by NoTiG on 2007-04-22
just wondering... when move a window and it wobbles the windows look jaggy. is this fixable with the video card driver more so... or is it some feature that will need to be implemented in beryl/compiz ?

---

### Post by Stickymaddness on 2007-04-23
Sounds like you have the compiz desktop effects enabled.

Go System->Pref->Desktop Effects and disable it.

---

### Post by centy on 2007-04-23
I think he wants the desktop effect, but with less aliasing on the edges.

What graphics card do you have? 
I have a nvidia card, there are settings for antialising in the control panel (using the restricted drivers NVIDIA accelerated graphics driver 9631) although I don't know if these effect the desktop effects. 
You can access this control panel by typing the following into the terminal
```
sudo nvidia-settings
```
input password and press enter.

---

### Post by NoTiG on 2007-04-23
thanks for the reply. i tried it and set anti aliasing to 16X and it didn't make a bit of difference. guess its something that will need to be addressed through cairo or the windowing system or whatever.

---

### Post by bartaz on 2007-04-23
Antialiasing can be set in nvidia-settings but to make it visible you need to load settings before starting beryl/compiz.

So run
```
nvidia-settings
```
set anything you need there (don't make antialiasing 16x because it will be really slow).

Then run
```
nvidia-settings -l
```
that will load settings. Now you need to rerun your beryl/compiz window manager.
I use beryl-manager for that.

If you want to make it on session start add nvidia-settings -l to your System > Preferences > Sessions.

Anti aliasing can make system slow, so play with settings to make it look & feel good.

You can find more here:
[http://forum.beryl-project.org/viewtopic.php?f=39&t=2433&start=0]("http://forum.beryl-project.org/viewtopic.php?f=39&t=2433&start=0")

---

### Post by igknighted on 2007-04-23
also, you can install a program called nvclock.  It is primarily used to overclock your nvidia card, but also has applications here.  Once it is installed, type "nvclock -a fsaa=#" where # is the desired AA setting, 0-9 (9 being most AA).  Made a huge difference for me when nvidia settings did nothing.

---

### Post by locke.dragon on 2007-04-27
how can i tell if i have an nvidia card?

---

### Post by the_axiom on 2007-04-27
how do I change anti-aliasing on ati?

---

### Post by locke.dragon on 2007-04-27
i think i have an ati card, but i'm not sure.  could someone post a terminal script that will tell me?  i know it exists, i just can't find it.  :P

---

