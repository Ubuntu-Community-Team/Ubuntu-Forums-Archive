---
title: "White Cube"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by noisebug on 2007-12-19
I'm a beginner, so take it easy on me. ;)

Installed 7.10, installed NVIDIA Restricted Drivers with Compiz. All worked great. I wanted to install WoW so got Cegea on here, but I failed the OpenGL test. 

I thought this was a driver issue, so i uninstalled restricted drivers and installed NVIDIA drivers. Upon reboot, I get the white cube. I can spin it, see skydome, but the cube itself is white.

I can get into terminal with CTRL-ALT-F1 but I'm not sure where to go from here. 

Any suggestions?

PS: I searched around the net, but most fixes seem to be for beryl and ATI cards. I have not found a solution.

Thanks in advance

(NVIDIA 8800 GTX)

--EDIT--

I hit ALT-F2 and ran "compiz --replace".
It DID load my desktop, but none of the effects we're enabled. Though Cedega does say 3D acceleration is enabled, just not Open GL.

--EDIT 2--

I tried installing the Restricted Drivers Again when I got my desktop back. I did not uninstall the old nvidia drivers because I did not know how. Anyway, when I reboot I still get the white cube. Whats worse, I cannot do "compiz --replace" anymore. When I do that, I see my desktop for 2 seconds and it goes white again. :( I give up for tonite!

---

### Post by CatKiller on 2007-12-19
That is a driver issue. I've seen that happen in the past when drivers have not been correctly installed. There are other threads about it, I think. The way to remove the drivers that caused the problem, I suspect, depends on how you installed them. I've only ever installed the driver through Synaptic, so I can't help you with that, but hopefully someone who's used the same install method as you will be able to show you the way.

---

### Post by noisebug on 2007-12-19
Thanks for your reply.

I installed and uninstalled the restricted drivers through the restricted driver manager. I installed the NVIDIA drivers in command prompt through the NVIDIA installed. I received no errors or problems in the installation. I then tried reinstalling the restricted drivers through the manager, but that didn't help at all.

---

### Post by lswest on 2007-12-19
well, since im not 100% sure of how best to uninstall the drivers, you can go into the terminal view and change in /etc/X11/xorg.conf (open it with ```
 sudo vim /etc/X11/xorg.conf
``` )
then find the line that says driver "nvidia" and change it to driver "nv", which should get you your desktop back after a reboot.  from there on you can uninstall the drivers and get the right ones working again.

---

### Post by noisebug on 2007-12-19
I got to the desktop. Uninstalled NVidia drivers, and installed restricted... these drivers use to work just fine, but now, I get the white screen again. I uninstalled restricted, installed nvidia. I also reinstalled compiz and emerald, again, white screen.

Nothing seems to be working, I'm at a loss. Maybe I'll just reinstall... would like to stay away from that if possible though.

---

### Post by lswest on 2007-12-20
try completely removing all the graphics drivers for the time being, and then try (after a reboot) to install the drivers that originally worked for you.

---

### Post by CatKiller on 2007-12-20
It might also be worth, after you've uninstalled the drivers, seeing where /usr/lib/libGL.so.1 points to. I've seen that get confused before, and point to the wrong file - which is largely where the white cube comes from, as far as I can tell; instead of the right library being called, one that doesn't handle the textures in the expected fashion gets called instead, and subsequently no textures get drawn at all. The cube still gets drawn, but it is white.

---

