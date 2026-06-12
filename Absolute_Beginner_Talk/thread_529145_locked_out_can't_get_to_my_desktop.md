---
title: "locked out can't get to my desktop"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by kerrymorgan1 on 2007-08-18
ive been trying to install beryl i followed instructions went fine but i couldn't add something to start up i wanted to check it out to see if it would matter (actually checking to see if i installed everything right)

it wouldn't let me in (would just go black and wouldn't load Ubuntu) 
i entered 
```

sudo dpkg-reconfigure xserver-xorg

```

pushed enter right through that
 
```

sudo reboot

```

and nothing changed still can't get in

i have an Nvidia 8600gt i tried reiinstalling the drivers the same way i initially did and still nothing can someone help please?

---

### Post by taurus on 2007-08-18
Try reconfiguring X again from a recovery mode from GRUB menu.

```
dpkg-reconfigure xserver-xorg
shutdown -r now
```

---

### Post by kerrymorgan1 on 2007-08-18
when i enter
```

sudo /etc/init.d/gdm stop
cd Desktop
sudo sh NV (press tab)
sudo /etc/init.d/gdm start

```

this is the path i followed to install Nvidia drivers
i did it again and nothing

i tried 
```

dpkg-reconfigure xserver-xorg
shutdown -r now

``` 

but still the issue is the same.... should i be changing the settings there?

---

### Post by taurus on 2007-08-18
I think the problem here is beryl!  Therefore, you need to reconfigure /etc/X11/xorg.conf again.  Then, reinstall nVidia driver for it.  Unless you did save a copy of /etc/X11/xorg.conf before you installed beryl, you can just copy it back.

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by kerrymorgan1 on 2007-08-18
> **taurus said:**
> I think the problem here is beryl!  Therefore, you need to reconfigure /etc/X11/xorg.conf again.  Then, reinstall nVidia driver for it.  Unless you did save a copy of /etc/X11/xorg.conf before you installed beryl, you can just copy it back.

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

just so i don't type anything i shouldn't what are the exact cod i put in after the code above you just mentioned?

---

### Post by kerrymorgan1 on 2007-08-18
i typed in that code.... tryed to reinstall the the Nvidia drivers.... tried to start the desktop again but a window has popped up again....

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. would you like to view the X server out put to diagnose the problem?"

but when i click yes to that it says the xserver not found that i need to install it again ....

i know this is Linux and not windows but should i just reinstall Ubuntu again?

---

### Post by taurus on 2007-08-18
Press <Ctrl><Alt>F2 and log in with your name and password.  Then, reconfigure X again with

```
sudo dpkg-reconfigure xserver-xorg
```
Once you are done with it, see if X is running now with

```
startx
```

---

### Post by tipiglen on 2007-09-13
Same problem, or similar.

After first install from scratch (6.06.1) from hard disk, cause cdrom is very dodgy, everything worked fine at first boot, but every boot since then, it gets through login and password, and just sits there with maroon background and movable mouse pointer.

ctr//alt/f2 gets terminal, but any sudo prefixed commands just hang with flashing cursor.

ctrl/alt/del starts shutdown, but that hangs at deconfiguring networks.....

Help!

ed

---

