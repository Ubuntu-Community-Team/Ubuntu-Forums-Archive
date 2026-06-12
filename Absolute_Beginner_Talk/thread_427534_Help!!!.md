---
title: "Help!!!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by sewercake on 2007-04-29
HI

I was trying to install some radeon 9250 drivers onto my computer, and when I restarted it was all screwy and said something about X, then it went to the command prompt, how do I get the graphic settings back to default?
thanks for all your help



-sewercake

---

### Post by taurus on 2007-04-29
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mikewhatever on 2007-04-29
Can you post the output of 
> ls /etc/X11

I am trying to determine if there is a backup of xorg.conf file, which contains the graphic settings.

---

### Post by sewercake on 2007-04-29
It come up with no such file or directory when I did the x11 thing, when I tried the dpkg, i was going though the configure, when at the colour depth, it came up with xserver-xorg postinst warning, and I couldn't get back to the configurer.
thanks for the help




-Sewercake

---

### Post by taurus on 2007-04-29
Look at the command again especially about the capital X before number 11.

---

### Post by sewercake on 2007-04-29
ahhhh, ok. it was the capital X, i ran an ls, and I found a xorg.conf.original-0 file, shall I run it? And i will post up the whole findings, but I can directly copy paste
> 
app-defaults
cursors
default-display-manager
fonts
gdm
rgb.txt
X
xinit
xkb
xorg.conf
xorg.conf~
xorg.conf.20070429132631(more of these but I will only post them up iif needed)
xorg.conf.fglrx-0
xorg.conf.original-0
Xresources
xserver
Xsession
Xsession.d
Xsession.options
Xwrapper.config


THere, thanks for the help you guys



-Sewercake

---

### Post by sewercake on 2007-04-29
Darn, is anyone still there?

---

### Post by taurus on 2007-04-29
```
sudo cp /etc/X11/xorg.conf~  /etc/X11/xorg.conf
```

---

### Post by sewercake on 2007-04-29
I tried that, and nothing happened, it just popped up with another thing to type a command into.
thanks



-Sewercake

---

### Post by taurus on 2007-04-29
What happens when you try

```
startx
```

---

### Post by sewercake on 2007-04-29
comes up with some info. then says 
> 
fatal server error:
no screens found
X10: fatal IO error 104 (connection rest by peer) on X server ":0.0"
        After 0 requests (0 known processed) with 0 events remaining

That does not sound good :( 
and if there is no way to fix this, I could just re-install linux
cheers



-Sewercake

---

### Post by taurus on 2007-04-29
Try

```
sudo cp /etc/X11/xorg.conf.original-0  /etc/X11/xorg.conf
startx
```
_Otherwise_, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by sewercake on 2007-04-29
YESSSSSSSS
thank you very much taurus! you rock!
cheers




-Sewercake

---

