---
title: "update to gusty, nvidia driver will not load."
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by jaybombalous on 2007-10-10
Ok here is the problem, I just updated to gusty last night. Ever since then when X starts to load I always get this black screen that has a login prompt, this screen flashes up 2 - 3 times and then finally I get this weird message that says, low graphic resolution. Ask me if I wanna configure xorg, shutdown, or continue.

Doesn't matter what you do, it always starts X with xorg.conf.failsafe. 

I have the restricted modules driver loaded, it says its in use, but if I type 

```
sudo nvidia-settings
```

it tells me that it doesn't seem that there is a X server using the nvidia driver.

Now that tells me there is something very strange going on. But I just don't know how to fix it.

I am new to linux, but not computers, so someone please explain this to me or help me figure out what I did wrong. 

The only problem I see now is the fact that I tried fixing this myself and probably created more problems then I originally had. I have tried to undo most of them. :)

Please don't tell me to fresh install either... that doesn't help me learn how to use this thing, now does it?

---

### Post by renzokuken on 2007-10-10
you dont need to do a fresh install, just reinstall the nvidia drivers.

everytime you update/change the kernel, you need to reinstall the nvidia driver

---

### Post by jaybombalous on 2007-10-10
well I got it fixed, but reinstalling the drivers through the restricted modules didn't work. In fact nothing I had tried worked until I seen the hack for Envy and ran that.

One reboot later and all was well. I have no idea what was causing all my problems. Thanks god for third party software that actually works.


But that is not the only quirk happening, now audacious won't load any of its settings even though there is a .audacious folder in my home dir. Wonder what it will be next???

:confused:

---

### Post by jrny99 on 2007-10-13
please tell us where this hack is, i have the same problem ? 

:confused::confused:

---

### Post by juicymixx on 2007-10-18
okay, I'm having this exact same issue.   starting up gusty happens exactly as you described.   If I try to run 
nvidia-settings
I get a box saying:
You do not appear to be using the NVIDIA X driver.   Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
running nvidia-xconfig says that it's making changes to the xorg.conf file, however an X server restart always falls back to the failsafe.

What did you do to get this fixed?:confused:

---

### Post by juicymixx on 2007-10-18
> **juicymixx said:**
> What did you do to get this fixed?:confused:


I found a/the solution.   Installing envy 0.9.8 then running it fixed everything.
I'm not sure what was wrong to begin with, but envy fixed it all up.

Hurrah for Alberto Milone!!:)

---

### Post by jrny99 on 2007-10-18
Try running sudo nvidia-settings.

---

### Post by maxxym on 2007-10-18
Guys, read my post about this. I got this working....there is another post about the same problem and I posted solutions in there.

---

### Post by sharp65 on 2007-10-18
I can't enable the Nvidia restricted driver either, whenever I click enable then enable driver it tells me "the software for nvidia-glx-new is not enabled". running sudo nvidia-settings does nothing.

---

### Post by juicymixx on 2007-10-19
> **jrny99 said:**
> Try running sudo nvidia-settings.jrny99: because x would fail to failsafe, nvidia-settings would always return
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

> **maxxym said:**
> there is another post about the same problem and I posted solutions in there.maxxym: I searched before I posted and didn't find anything else relevent to my problem.   I probably missed it.   Could you post a link?

---

### Post by maxxym on 2007-10-19
Sure..

[http://ubuntuforums.org/showthread.php?t=580308](http://ubuntuforums.org/showthread.php?t=580308)

---

