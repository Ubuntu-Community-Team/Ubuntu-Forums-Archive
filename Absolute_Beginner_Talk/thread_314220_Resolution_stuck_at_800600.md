---
title: "Resolution stuck at 800*600"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by LIJI on 2006-12-07
Hey, I'm pretty new the Ubuntu (Installed Linux for the very first time this week! :D), So please make it simple.

When I was using the Live CD the resolution was pretty random all time:
Once it was 1280*1024 ( The correct one ), Once it was 1024*768 and once 800*600 (Horrible!).

My Ubuntu version is 6.10.

I'm using an LCD, and it only looks good on 1280*1024.

I tried reinstalling Linux, but it just became worse (It became from 1024*768 to 800*600).

Please help me.

Btw, If you need me to give me some information, please make sure to tell me how to check it on Linux! ;)

Thanking in advance,
-LIJI

---

### Post by taurus on 2006-12-07
What video card do you have?  You probably need to install a driver for it so you can go with a higher resolution.

---

### Post by LIJI on 2006-12-07
You mean Graphics card? I'm pretty sure it's GeForce FX.

---

### Post by Ecthelion on 2006-12-07
Hi.

You might have to reconfigure your x-server.

Press Ctrl-Alt-F1 to go to a terminal. (Pressing Ctrl-Alt-F7 should bring you back to the graphical interface)
Do
```
sudo cp /ect/X11/xorg.conf /etc/X11/xorg.conf_back
```
to backup your xorg.conf file
Then do
```
sudo dpkg-reconfigure xserver-xorg
```
and answer the questions.
When they ask wich resolutions to use add those you want, but make sure your monitor can have those resolutions.

If you messed it up you can go back to your old settings by typing
```
sudo cp /ect/X11/xorg.conf_back /etc/X11/xorg.conf
```

---

### Post by taurus on 2006-12-07
Here you go for the nVidia card...

[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

### Post by LIJI on 2006-12-07
@Ecthelion I tried it before, it didn't work
@taurus I installed it now, I'm rebooting hoping it will work :)

---

### Post by LIJI on 2006-12-07
Ok, After rebooting Gnome failed to start because of some wrong settings in the XServer or something.
Luckily I still had "That Other OS Which is Really Bad and Starts With W" installed so I can post this reply.
How do I fix it now? :(

---

### Post by taurus on 2006-12-07
Boot into recovery mode from GRUB menu and post your /etc/X11/xorg.conf here...

```
cat /etc/X11/xorg.conf
```
Meanwhile, you can run these from the prompt.

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by LIJI on 2006-12-07
Ok, Thanks!
I got the whole thing to be fixed and my resolution is back to normal! :D

---

### Post by taurus on 2006-12-07
So you get your desire resolution now!

---

