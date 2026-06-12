---
title: "Login Help"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by basblplayr on 2007-11-12
I have been running Gutsy perfectly fine since it was released until today.  I shut down my laptop like normal and when I rebooted logged in as normal only to be met with a completely blank screen except for the mouse cursor.  I can move the cursor but nothing else works, ctrl+alt+f2 will not respond, and the only thing that responds is to press the power button which lets me log out.
I can, and am now, log in with the failsafe gnome option.  But, I would really like to have my fusion/emerald standard setup back!
I think the problem may lie somewhere in the startup scripts for Xclient, but I am fairly new to Ubuntu/Linux/Gnome and really can't diagnose problems like this by myself.
Any ideas?
Much thanks in advance.

---

### Post by infurnus on 2007-11-12
move xorg.conf
```

sudo mv /etc/X11/xorg.conf xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg

```
once you have setup the config files do
```

startx

```

go through setup if you're unsure which driver to use for the video card use vesa. Once you get in go here [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and get the correct drivers IF YOUR USING NIVIDIA OR ATI

---

### Post by basblplayr on 2007-11-12
Alright, I tried that.
I did the reconfiguration of the Xserver and that went fine.
When I went to do "xstart" it told me that the server was already running and gave me a lot of crap about it.
I have also since reinstalled all the packages for compiz, emerald, and the xserver with no results.
Sometimes, randomly it seems, when I try to login with the Xclient scripts session, it will display the icon for Ktorrent, but with no functionality and nothing else on the screen but the mouse cursor and a black background.  I got the gnome panel to work once by starting it at a command line, but nothing came from it really.
Sorry to be difficult, any other ideas?

---

### Post by basblplayr on 2007-11-12
And the video card/driver is Intel integrated graphics on a G965 chipset.

---

### Post by ruibernardo on 2007-11-12
Instead of "startx", make sure you logout from Gnome, press Alt+Ctrl+F1 to go to a tty console, login and try

```
sudo /etc/init.d/gdm restart
```

---

