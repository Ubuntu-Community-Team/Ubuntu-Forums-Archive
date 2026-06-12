---
title: "3D graphics problem"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by deuchar1 on 2007-03-22
Hey guys,

I'm needing a little help getting 3d support for my nvidia Geforce FX 5200 card.
I've tried numerous suggestions now including Envy autosetup utilities and so forth, and every single one breaks my system and puts me in a command line on restart with errors.

Does anyone know a foolproof way of getting this card 3D enabled? I want to play SuperTuxKart :P  

Cheers,
Graham

---

### Post by jem7v on 2007-03-22
What errors are you getting, specifically?

My solution in the past has been to run the Envy script to get all my dependencies handled, and then let the actual NVidia installer do the driver itself, because Envy never does a good job picking and installing the right driver for my system (but it downloads all the dependencies I need to install it and compile the proper kernel with the NVdia installer).
Get it here. [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use it, go into a console (i.e., Ctrl+Alt+F1), log in, and stop your X server by doing:
```
sudo /etc/init.d/gdm stop
```
Then go to the directory you downloaded the script into and run it with
```
sudo sh (scriptname)
```
and hope that it works.  Then check your xorg.conf file to make sure it has the nvidia driver instead of nv listed under Device with
```
sudo nano /etc/X11/xorg.conf
```
and then turn your X server back on with
```
sudo /etc/init.d/gdm restart
```
and see what happens.

---

### Post by justleen on 2007-03-22
i have always managed to get this up and running with the guides of TSElliot  ( =D> )
check his website for the guides
[http://albertomilone.com/guides.html](http://albertomilone.com/guides.html)

---

### Post by srt4play on 2007-03-22
Call me crazy but why not install nvidia-glx from synaptic and then change 'nv' to 'nvidia' in /etc/X11/xorg.conf?

---

### Post by jem7v on 2007-03-22
Because sometimes it doesn't work, and those drivers are consistently older than the drivers on the NVidia site.

---

### Post by deuchar1 on 2007-03-23
Got it working! I had a previous dodgy install of Envy which seemed to be cocking things up a little - that's why when I re-ran it I got nothing but errors and X server died a death. I used Envy's inbuilt uninstaller to clean the system of all the previous junk and tried it again with a bit more luck this time!

One thing I did wonder about - what is the dpkg-reconfigure thing the xorg.conf thing goes on about? It says if I don't run it automatic updates won't happen because I've manually edited the file. Is this a problem or is all good anyway?

Last thing - I have a new Linux image - meaning there are now several in my Grub booter. Can I safely remove these through Synaptic to get them off the menu?

Cheers,
G

---

