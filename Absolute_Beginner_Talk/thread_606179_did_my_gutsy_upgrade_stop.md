---
title: "did my gutsy upgrade stop?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by finer recliner on 2007-11-07
i'm trying to upgrade from feisty to gutsy, but i think my upgrade froze or something. i used update-manager to run it. i got to the point where update manager wanted to do a partial upgrade (?) and download 729 updates. attached is a screen shot of what is currently going on. i tried running do-release-upgrade, but the other update is already running, so it wont work. 

should i just restart my computer and try again? i dont want to screw it up if i dont have to...

---

### Post by tdrusk on 2007-11-07
that sucks.

I would close the process, run
```
dpkg --configure -a
```
Now go to your update manager and try again.
Don't rebot unless 100% necessary.

---

### Post by finer recliner on 2007-11-08
it wouldnt let me kill the upgrade processes (even with kill -9). so i burned the iso and just reformatted and installed fresh

(after backing up my data first of course hehe)

thanks anyways

---

### Post by tdrusk on 2007-11-08
> **finer recliner said:**
> it wouldnt let me kill the upgrade processes (even with kill -9). so i burned the iso and just reformatted and installed fresh

(after backing up my data first of course hehe)

thanks anyways
good choice

---

### Post by Seisen on 2007-11-08
Wait till the other update finishes then do the ```
sudo do-release upgrade
```

---

### Post by joehill on 2008-02-22
Same thing happened to me, and this has probably happened every time I've tried upgrading Ubuntu. Previous times I've just stopped the process and done a fresh install, but this time I killed the process it was hanging on, and the install continued.

This time, it hung at the "Stopping Bluetooth . . ." stage.  So I opened a terminal and killed the process in question (something like "/etc/init.d/bluetooth stop"). Installation then continued as desired.

I wish there were a timeout feature to the upgrade process--that would save a lot of people from hosing their system.

---

