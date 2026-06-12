---
title: "Trouble installing ATI Drivers"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Heous on 2007-03-08
Hello everyone.  I recently downloaded the most recent drivers for my ATI Radeon X1800 card, but for the life of me I can't figure out how to install them.  It's a .run file, and the default installation methods (synaptic and gedit) don't seem to apply to it.  If anybody knows how to explain how to install a .run file, it will be much appreciated.

---

### Post by igknighted on 2007-03-08
Is there any reason you are using the ones from ATI's site?  I think the ones in the repos are the same version, but in nice debian packages ;-).  Try these simple steps in the terminal:
```
sudo aptitude update
sudo aptitude install xorg-drivers-fglrx
sudo aticonfig --initial
```

and then restart.  Once the system is back up, test the install with:
```
glxinfo | grep direct
```
it should say yes and:
```
fglrxinfo
```
It should talk about ATI and make no reference to "mesa".

Now delete the driver you got from ATI and you are good to go.

---

### Post by Einherjer on 2007-03-08
tag

---

### Post by Heous on 2007-03-08
Seems pretty good, thanks for the help.

---

