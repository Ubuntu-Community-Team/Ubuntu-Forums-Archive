---
title: "rs.local____[Fail]  no bootup :("
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by dmxsoulja3 on 2007-11-21
Guys I'm not sure whats going on, I wake up this morning fire up my machine running Gutsy and I get a line which if I remember correctly said something along the lines of an unexpected line in rs.local then off to the right hand side it said FAIL in red, and it would boot up to low graphics mode only.  I'm using the ENV driver and I haven't made any changes or anything this just seems all of a sudden, is there anyway to recover or am I looking at a reinstall of ubuntu?

---

### Post by Dr Small on 2007-11-21
> **dmxsoulja3 said:**
> Guys I'm not sure whats going on, I wake up this morning fire up my machine running Gutsy and I get a line which if I remember correctly said something along the lines of an unexpected line in rs.local then off to the right hand side it said FAIL in red, and it would boot up to low graphics mode only.  I'm using the ENV driver and I haven't made any changes or anything this just seems all of a sudden, is there anyway to recover or am I looking at a reinstall of ubuntu?
Hmm. It would be rc.local. But anyhow, that is one of your startup scripts... I wonder what could be wrong with it, or how to fix it.

Edit: Since it went into safe graphics mode, it looks more like a problem with X or Gdm.

---

### Post by dmxsoulja3 on 2007-11-21
yeah I'm not sure, the only thing I did was the recommended ubuntu updates but I assume if there was a problem alot more people would be posting about it.  but yeah sure enough I'm low graphics mode only, and its hit or miss if it will even start up.... interestingly enough I was touting to my friends about Uptime, I was at like 58 days, I wake up, I went to open Firefox, nothing, so I restarted my X session, re login, and it just spins on the tan screen.....I shut down, restart, and thats when I get the rc.local issue.

---

### Post by Dr Small on 2007-11-21
Ok. It is sounding more and more like X.
Could you try reconfiguring xserver-xorg ?

First, just to be on the safe side, in case it *isn't* xserver-xorg, let's make a backup of the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.11.21.07
```
Now, to try to reconfigure xorg, run:
```
sudo dpkg-reconfigure xserver-xorg
```

Dr Small

---

### Post by dmxsoulja3 on 2007-11-21
yeah I will try that when I get off work, can you also tell me what command lets met get into the xorg.conf to modify it? because when I reconfigure it with ENV installed you have to edit a line and I don't remember how to get back in there.   This sucks I finally had my whole system setup how I wanted lol

---

### Post by Dr Small on 2007-11-21
> **dmxsoulja3 said:**
> yeah I will try that when I get off work, can you also tell me what command lets met get into the xorg.conf to modify it? because when I reconfigure it with ENV installed you have to edit a line and I don't remember how to get back in there.   This sucks I finally had my whole system setup how I wanted lol
From the command line:
```
sudo nano /etc/X11/xorg.conf
```

From GUI:
```
gksudo gedit /etc/X11/xorg.conf
```

Dr Small

---

### Post by dmxsoulja3 on 2007-11-21
Alright cool I will let you know how it goes, worst case scenario I have been wanting to try out dream linux :)

---

