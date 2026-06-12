---
title: "Error--Failed to initialize HAL"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-04-22
what does this error mean?

It prevented Ubuntu from loading the first time, but the second time I clicked OK and it loaded after that.

What needs fixed or deleted?

---

### Post by mabelrxu on 2007-04-22
ooo ... that sounds nasty ...

um ... HAL is a list that tells your software how to interact with your hardware ... maybe that will help you come up with some ideas for fixing it ... :-k

sorry i can't help more ... i've never ever run into this ever before ...

---

### Post by Vomit-Orchestra on 2007-04-22
Eeep. What did you do?
I suggest reinstalling, just to be on the safe side O_O

---

### Post by mabelrxu on 2007-04-22
yeah ... i didn't want to alarm you, but reinstalling's probably the best option

btw, if you install /home into it's own partition, then you won't erase over your files and settings on clean installs in the future ... :)

---

### Post by t2000kw on 2007-04-23
I'm not sure how to move the folder to another partition, or to install with that option. 

However, Hal is gone, at least for now. I did a complete restart since my wife was in Windows and I didn't see the message. 

I was thinking about installing Edgy Eft, though. Can you have another kernel installed without overwriting everything and starting all over again?

---

### Post by mabelrxu on 2007-04-24
yes ... if you have internet working, just do a sudo apt-get update and a sudo apt-get dist-upgrade ... I think that updates your kernel ... and here's a tutorial for moving your /home folder to another partition: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) ... or, you could do it when you do a reinstall

---

### Post by CMcGarity on 2007-05-04
To fix this error, Ctrl-F1 over and login. Enter these commands:

sudo update-rc.d -f dbus remove

sudo update-rc.d dbus defaults 12

Presto! I did a shutdown -r now, but that was me being extra precautious. You should boot up and be A-OK.

CMcGarity (at) GMail (dot) com

---

### Post by mabelrxu on 2007-05-04
> **CMcGarity said:**
> To fix this error, Ctrl-F1 over and login. Enter these commands:

sudo update-rc.d -f dbus remove

sudo update-rc.d dbus defaults 12

Presto! I did a shutdown -r now, but that was me being extra precautious. You should boot up and be A-OK.

CMcGarity (at) GMail (dot) com

that guys sounds like he knows what he's talking about ... if it was me, I would definitely try it ... but if you do have to reinstall, having all your settings remain (because you've moved your /home or made a backup) cuts the frustration down by at least half (the other half is reinstalling all your programs ^_^ )

good luck!

---

### Post by everdred on 2007-05-11
> **CMcGarity said:**
> To fix this error, Ctrl-F1 over and login. Enter these commands:

sudo update-rc.d -f dbus remove

sudo update-rc.d dbus defaults 12

Presto! I did a shutdown -r now, but that was me being extra precautious. You should boot up and be A-OK.

CMcGarity (at) GMail (dot) com

Just tried this and it worked for me.

---

### Post by t2000kw on 2007-05-11
Believe it or not, I fixed this error by simply rebooting. No errors when loggin into Gnome.

---

### Post by ckoester on 2007-05-20
I received this error after installing LinuxMCE.  CMcGarity's solution worked for me.  Huge thanks!

---

