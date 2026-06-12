---
title: "Nvidia drivers"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by cumanzor on 2007-04-09
Hi! I have a GeForce 4 MX 4000, and I installed the drivers using System>Administration>Restricted Driver Manager.


Seems to work fine, since beryl works perfect, but, I can't change the resolution, other than 640x480 and 800x600. I used XP in 1280x960 resolution. Changing the xorg.conf doesn't work.

What can I do?

---

### Post by JAPrufrock on 2007-04-09
Try running the following command in terminal: 
> sudo dpkg-reconfigure xserver-xorg
If you don't know how to choose some of the options, leave them the way they are.

---

### Post by censored77 on 2007-04-10
I've had a very similar problem, not yet resolved. [This ]("http://ubuntuforums.org/showthread.php?t=404975&highlight=resolution")thread has some advice about getting the latest drivers, which I haven't had chance to try yet.

---

### Post by kc5hwb on 2007-04-10
You have to stop GDM before running that cmd.  So this..

```
sudo /etc/init.d/gdm stop
```

Then run the reconfigure command listed above.  Then when that is done, restart GDM with this...

```
sudo /etc/init.d/gdm start
```

---

### Post by cumanzor on 2007-04-10
Great!

It worked, but I still need to add a custom refresh rate; 1280x960 at 70hz, how do I do that?

edit: No idea what happened, but now I'm getting this error while trying to start beryl:
also, the alternative group keys don't work anymore (alt gr + 2 for @)

> Xlib:  extension "GLX" missing on display ":0.0".


edit2: Back in my 800x600 only xorg.conf. Beryl works and also the alt gr keys... I'm confused. :(

---

### Post by JAPrufrock on 2007-04-10
Try  reinstalling the nvidia driver to get 3d acceleration working again.

---

