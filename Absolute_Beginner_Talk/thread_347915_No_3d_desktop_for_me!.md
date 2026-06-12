---
title: "No 3d desktop for me!"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by kj1h234lkj1234 on 2007-01-28
Hi.

I cannot use Beryl: after enabling it, my entire system locks up after about 5 seconds (necessitating a hard reboot).

I cannot use Compiz: it messes with the keymaps, and I need to be able to use the Finnish keyboard layout in addition to the US one.

Suggestions?

Kiitos :P

---

### Post by MkfIbK7a on 2007-01-28
what is your graphics card?

---

### Post by r4ik on 2007-01-28
For the keyboard,

System-Preferences-Keyboard-layouts-add

Good luck !

---

### Post by kj1h234lkj1234 on 2007-01-28
> what is your graphics card?
I knew I forgot something -> nvidia GeForce FX 5950 Ultra (256mb)

Will adding the additional keyboard layouts still work after all that xmodmap crap?

From: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29)
> #!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
**xmodmap /usr/share/xmodmap/xmodmap.us**

Thanks!

---

### Post by r4ik on 2007-01-28
For youre card try ,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Cant tell you about the keyboard give it a try :)

Good luck !

---

### Post by kerry_s on 2007-01-28
You can try 3ddesktop(sudo apt-get install 3ddesktop) in the repos, it's kinda like the poor system's special effects. Here's the app page to look at the screen shots-> [http://desk3d.sourceforge.net/screenshots.php](http://desk3d.sourceforge.net/screenshots.php)
It use to be the popular thing back in the day. You can type 3ddesk to launch it. I usually make a launcher with the settings i want, 
example: 
3ddesk --mode=random --zoomspeed 10 --changespeed 10

use> man 3ddesk < in terminal to read all the settings.
left right mouse button to move left or right and middle click to select, you can also use the arrow keys.

---

### Post by kj1h234lkj1234 on 2007-01-28
Thanks for the suggestions! :)

---

### Post by m1215 on 2007-01-28
like someone said above, try the nvidia driver. i have a fx5600 ultra 128 mb and both compiz and beryl work good. also xcompmgr works good just not a lot of fancy stuff.

---

### Post by kj1h234lkj1234 on 2007-01-29
> **m1215 said:**
> like someone said above, try the nvidia driver. i have a fx5600 ultra 128 mb and both compiz and beryl work good. also xcompmgr works good just not a lot of fancy stuff.

I do have the nvidia driver installed properly (I need it to play Quake 3 ... :) ), but Beryl still randomly locks up my entire machine a few seconds after I activate it. All my other graphical programs work fine.

---

### Post by muguwmp67 on 2007-01-29
Is Xgl installed? And are you selecting xgl from your login window?

---

