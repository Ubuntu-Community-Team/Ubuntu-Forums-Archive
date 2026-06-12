---
title: "Just installed new graphics drivers, computer wont boot"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by nzk on 2006-08-21
Help! I just installed those ati graphics drivers andnow, for some reason, my computerwont get past the login screen,which isnt a screen anymore but a bunch of text.

It says something like "x server problem"

---

### Post by Iarwain ben-adar on 2006-08-21
Hi,

try this:
```
sudo dpkg-reconfigure xserver-xorg
```


Iarwain

---

### Post by nzk on 2006-08-21
nope that doesnt work :(

---

### Post by Jax55 on 2006-08-21
I think this is the result of a dodgy upgrade package - See the thread

[http://ubuntuforums.org/showthread.php?t=240957](http://ubuntuforums.org/showthread.php?t=240957)

There are some tips on how to revert the xserver-xorg-core package back to the last working version.

I just lost 2 working machines to this one!  *sigh*

---

### Post by JedV on 2006-08-21
> **nzk said:**
> Help! I just installed those ati graphics drivers andnow, for some reason, my computerwont get past the login screen,which isnt a screen anymore but a bunch of text.

It says something like "x server problem"



Heh, I did the exact same thing... installed ATI drivers, and thought that it pooched my OS.  Thankfully there are great forums for us noobs.

---

