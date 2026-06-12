---
title: "Compiz water plugin"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Yes_It's_Me on 2006-07-07
Hi, i know that this plugin in unstable but i would like to give it a go, how do i enable it? Thanks!

---

### Post by nalmeth on 2006-07-07
Do you have the gsetcompiz app running in your system tray?

---

### Post by Yes_It's_Me on 2006-07-07
dont think so, never heard of it. everything works except for the water effects.

---

### Post by jordanmthomas on 2006-07-07
How did you go about installing compiz?
(From source or from packages?)

---

### Post by Yes_It's_Me on 2006-07-07
through packages, i used [http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

but when i type in sudo apt-get install gset-compiz, it cant find it, is there another repository i must add?

Thanks

---

### Post by jordanmthomas on 2006-07-07
```
deb http://xgl.compiz.info/ dapper aiglx
deb http://xgl.compiz.info/ dapper main

```
These are what I added and gset-compiz is in there.

---

### Post by Yes_It's_Me on 2006-07-07
i added those but still not there.

here is my apt sources list

EDIT: nethermind, got it, thanks guys

---

### Post by jordanmthomas on 2006-07-07
Did you do a 
```

sudo apt-get update

```

---

### Post by Yes_It's_Me on 2006-07-07
yeah that was the problem, cheers

---

### Post by jordanmthomas on 2006-07-07
Hope it's not too late...but if you're running XGL and not AIGLX you DO NOT want to install the compiz stuff that was in those repositories.  gset-compiz should be ok but you may want to look in the repositories to see which one has gset-compiz and get rid of the other so you don't accidentally put a non-working compiz in.  You'll probably be ok though.

---

### Post by Yes_It's_Me on 2006-07-07
everything seems fine, water effects are cool

---

### Post by jordanmthomas on 2006-07-07
good.  The water effects are pretty neat, but not as useful as the rest of the plugins.  Still, it's enabled on my computer.:p

---

