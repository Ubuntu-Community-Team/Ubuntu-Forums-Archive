---
title: "[SOLVED] desktop effects"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by mick222 on 2007-11-03
[SIZE="3"]Hi i'm new to linux tried Fedora  and 64bit ubuntu. Decided to go with 32 bit version .In fedora i liked the desktop effects , but can't seem to enable them in Ubuntu.I get an error "composite extension is not available" I have installed compiz as i thought it might include the missing extension can anyone help.[/SIZE]
Also is there a way to save a configuration , something like windows system restore.

---

### Post by overdrank on 2007-11-03
> **mick222 said:**
> [SIZE="3"]Hi i'm new to linux tried Fedora  and 64bit ubuntu. Decided to go with 32 bit version .In fedora i liked the desktop effects , but can't seem to enable them in Ubuntu.I get an error "composite extension is not available" I have installed compiz as i thought it might include the missing extension can anyone help.[/SIZE]
Also is there a way to save a configuration , something like windows system restore.

Hi could you tell us the model of the graphics card and which version of Ubuntu, Feisty 7.04, Gutsy 7.10?

---

### Post by Billy_McBong on 2007-11-03
[COLOR="Blue"]compiz fusion is installed by default in gutsy System>preferences>appearance>visual effects
you can install compiz settings manager to completely customize compiz
```
sudo apt-get install ccsm
```[/COLOR]

---

### Post by mick222 on 2007-11-03
I have an Amd64  3400x with a radeon9200 graphics card restricted drivers installed 512 mhz ram
I installed cssm but it didnt help would like to try the cube.
Running gutsy 32bit

---

### Post by overdrank on 2007-11-03
> **mick222 said:**
> I have an Amd64  3400x with a radeon9200 graphics card restricted drivers installed 512 mhz ram
I installed cssm but it didnt help would like to try the cube.
Running gutsy 32bit

Hi, you may try this link
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
It helped me on a ATI 9600. Good luck! :)

---

### Post by mick222 on 2007-11-03
I already have the proper ati drivers installed it seems to be the visual effects tab in appearances that has the problem

---

### Post by blueglue on 2007-11-03
1. Download "Gutsy"
2. Fresh install Gutsy
3. Enable desktop effects
4. Get bored, disable desktop effects & enjoy Ubuntu.

---

### Post by mick222 on 2007-11-03
Probably right blueglue but i did like the effect in fedora when you put the cursor in the top corner all windows showed especially scince Fedora uses spatial windows for file browsing.

---

### Post by overdrank on 2007-11-03
> **mick222 said:**
> I already have the proper ati drivers installed it seems to be the visual effects tab in appearances that has the problem

Ok, what is the output of this command in the terminal ```
fglrxinfo
```

---

### Post by mick222 on 2007-11-03
i hadn't installed fglrx was using restricted drivers from ati . Iinstalled it and get this info [SIZE="4"]OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6473 (8.37.6)

[/SIZE]

---

### Post by overdrank on 2007-11-03
> **mick222 said:**
> i hadn't installed fglrx was using restricted drivers from ati . Iinstalled it and get this info [SIZE="4"]OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6473 (8.37.6)

[/SIZE]

So you have DR now and the effects work?

---

### Post by mick222 on 2007-11-03
no effects still dont work i must have removed something think i might reinstall and get it right this time

---

### Post by mick222 on 2007-11-04
found the problem x server wasn't installed see this post [http://ubuntuforums.org/showthread.php?t=569654&highlight=xserver+gutsy](http://ubuntuforums.org/showthread.php?t=569654&highlight=xserver+gutsy)

---

