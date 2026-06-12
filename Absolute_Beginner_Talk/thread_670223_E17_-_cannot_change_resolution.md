---
title: "E17 - cannot change resolution"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by MaximB on 2008-01-17
have followed this guide : [http://forum.linux-hardcore.com/index.php/topic,1499.0.html](http://forum.linux-hardcore.com/index.php/topic,1499.0.html) and installed E17.
When I login to E17 the resolution is very high.
From what I've managed to read the problem is that my X-server is missing the support of the Randi extension and therefore the resolution cannot be changed...

This easy guide compiled everything from source, and I have a no idea how could I install this extension without  compiling from start.

What can I do ?

I have ATI 9800 Pro and I use property ATI drivers.
I also have a regular monitor (no LCD).

---

### Post by tzulberti on 2008-01-18
You could use the: sudo dpkg-reconfigure xserver-xorg to change resolution. In Gutsy, there is an option in System -> Preferences to change resolution. I dont know if that option appears in e17 menu.

---

### Post by MaximB on 2008-01-18
Even if I would assume that I know the answerers the the hundreds of questions that command asks, I could never even read them with that resolution. ;)
I am using the property ATI drivers and I afraid that this command will mess things up.

can't I just add this extension somhow ?

---

### Post by lswest on 2008-01-18
you could try installing enlightenment using the howto off [here]("http://ubuntuforums.org/showthread.php?t=20216"), since you really don't need to compile it from the source.  otherwise, i don't know where exactly the extension would be, maybe in the eutils package?

---

### Post by MaximB on 2008-01-18
it's 3 years old guide.
And if I already have E17 compiled and then I use a differet method to install E17 again, won't it make mess ?

---

### Post by smartboyathome on 2008-01-18
MaximB:
If I were you, I would uninstall E17 and then install it using [this guide]("http://ubuntuforums.org/showthread.php?t=546746") which is actually very easy and up to date. I wouldn't recommend using the guide linked to by lswest (no offense, lswest) as it is 3 years old.

---

### Post by Rui Pais on 2008-01-20
> **MaximB said:**
> have followed this guide : [http://forum.linux-hardcore.com/index.php/topic,1499.0.html](http://forum.linux-hardcore.com/index.php/topic,1499.0.html) and installed E17.
When I login to E17 the resolution is very high.
From what I've managed to read the problem is that my X-server is missing the support of the Randi extension and therefore the resolution cannot be changed...

This easy guide compiled everything from source, and I have a no idea how could I install this extension without  compiling from start.

What can I do ?

I have ATI 9800 Pro and I use property ATI drivers.
I also have a regular monitor (no LCD).

Hi MaximB. 
I found this thread incidentally... The method you used to install it's the same of smartboyathome link, but outdated. 
It points to my temporary repos, that i set when CafeLinux was down.

You should update repos cause the ones you have are not always uptode (i will update them after type this... but they are just temporarily)


About your issue, that means you have some incompatible resolution on your xorg.conf.
If the already suggested command dpkg-reconfigure ask to much questions you can run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` that it's simpler or edit xorg.conf by hand. You can do it from a console (CTrl+ALt+F1) if your resolution don't allow see the all screen.

---

### Post by MaximB on 2008-01-21
Never mind, trying the other guide

---

### Post by Rui Pais on 2008-01-21
> **MaximB said:**
> Never mind, trying the other guide

Hi, sorry the late answer.

How did it go?
I think problem may persist since that it's a xorg.conf/xrandr issue, not an e17.

If you need help editig xorg.conf by hand, just edit the lines started by "Modes" and put/leave there only the maximum resolution your monitor it's capable.

hth

---

### Post by MaximB on 2008-01-22
"Your" guide actually worked great ! but E17 is stil a little buggy.

---

### Post by lswest on 2008-01-22
haha, sorry about the out of date guide, i was kind of rushed, saw a good-looking thread, and slapped the link in the post:P i actually used another guide here to install E17 (just had to edit the source and change feisty to gutsy in the repos) worked well.

---

