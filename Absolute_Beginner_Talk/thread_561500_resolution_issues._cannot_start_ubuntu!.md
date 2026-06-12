---
title: "resolution issues. cannot start ubuntu!"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by mark. on 2007-09-27
i know that alot of people have asked this question, im sorry :/

but i was changing my resolution a while back using

```
 sudo dkpg -reconfigure -phigh xerver-xorg
```
and i changed it so that i can choose from all the different resolutions.
but after i closed the teminal that day, my comp shut down and i've been using xp since :/

i can only go into safe mode, since when i go into the regular one it says that xserver cant be started (something like that) and i cant type anything. it just freezes and reboots.

how can i fix this using only safe mode? and can i increase my resolution? (1280x1024 plx) i dont have a widesceen btw.

thx in advance mates :D

---

### Post by glotz on 2007-09-27
Try doing that same spell in safe mode and make different selections. Or restore the backups which you surely took of /etc/X11/xorg.conf before running it in the first place. :)

---

### Post by mark. on 2007-09-27
ok the thing is i ran
```
cd /ect/X11
```
but it said it couldnt find X11.....

so anyone who can help have a code that will allow me to change the resolution settings?

---

### Post by overdrank on 2007-09-27
> **mark. said:**
> ok the thing is i ran
```
cd /ect/X11
```
but it said it couldnt find X11.....

so anyone who can help have a code that will allow me to change the resolution settings?

HI you can try 
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by Linux_Man on 2007-09-27
Well make sure your at the root of the filesystem, because otherwise it will be in your home directory and etc/x11 isn't there, you will need to cd / before you go to the x11 directory.

---

### Post by glotz on 2007-09-27
> **mark. said:**
> ok the thing is i ran
```
cd /ect/X11
```

It's etc, not ect! :)

---

### Post by mark. on 2007-09-27
this is why i love linux!

im going to try this in safe. brb and ty

edit: ok i tried it, using 
```
sudo nano /ect/X11/xorg.conf
```
but the thing is that i can change the vaues and delete the resolutions that dont support my monitor,
how do i save after im done?? (sorry for my noobness)

---

### Post by ruibernardo on 2007-09-27
Hi Mark,

just press Ctrl+X (exit) and then Y (yes, you want to save the file).

But it's almost certain that this will not resolve your problem. You must reconfigure you xserver-xorg configuration and set the right frequencies of the monitor again. 

It was what you have began to do, but haven't complete. Please select only resolutions that you know that work. If you don't, repeat the process until you do. :-D

 To help a little more, take a look at this thread with a similar problem: [[SOLVED] Resizing]("http://ubuntuforums.org/showthread.php?t=557900").

---

### Post by mark. on 2007-09-27
ok so i got the horizrefresh and the other value (forgot what it was called)
30-70 and
50-160.

after i put that in the xorg.conf, and ended up playing around with the resolutions to see what works, i ended up setting all of then to 800x600 only.


it still didnt work *sob*

---

### Post by overdrank on 2007-09-27
> **mark. said:**
> ok so i got the horizrefresh and the other value (forgot what it was called)
30-70 and
50-160.

after i put that in the xorg.conf, and ended up playing around with the resolutions to see what works, i ended up setting all of then to 800x600 only.


it still didnt work *sob*

Hi what model graphics card are we talking about here?

---

### Post by mark. on 2007-11-12
its just a stock intel graphics card, on an old dell im using.

---

