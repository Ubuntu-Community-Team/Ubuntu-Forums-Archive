---
title: "why does sudo..."
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Sebastian1986 on 2006-07-01
Hey... just out of curiosity... 
sometimes  sudo does not ask for a password and sometimes it does 
can anyone explain...

---

### Post by T700 on 2006-07-01
[quote=Sebastian1986]Hey... just out of curiosity... 
sometimes  sudo does not ask for a password and sometimes it does 
can anyone explain...[/quote]

Your password is cached for a short time (10 minutes, I think is the default).  If security is a big concern, you can use a command line switch to kill the session before then.  I'm doing this from memory, but as I recall, it is "-K".

Paul

---

### Post by Sebastian1986 on 2006-07-01
is it possible to increase the amount of time ?

---

### Post by aysiu on 2006-07-01
[You can also change the timeout to be shorter.](http://www.ubuntuforums.org/showthread.php?t=183418)

---

