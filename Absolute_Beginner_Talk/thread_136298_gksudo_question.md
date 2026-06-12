---
title: "gksudo question"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-02-25
Okay, a while ago, I asked how to use *sudo* in a launcher.  Aysiu (thanks!) told me to use gksudo.  So far so good.

But when I plug in the command **gksudo nautilus /media/fatdrive** (for example) I get *Couldn't find "/'/media/fatdrive'".*  The same command without gksudo works as intended.  I don't get it :confused:

---

### Post by localzuk on 2006-02-25
have you tried this:

```
gksudo 'nautilus /media/fatdrive'
```

I believe the problem is due to the option (/media/fatdrive) being passed to nautilus. Putting it in ''s should allow it to be recognised as a single command IIRC.

---

### Post by Mustard on 2006-02-25
Yeah, I have experienced that issue myself.  I've commonly used the sudo gedit command to open some files, for example.. sudo gedit /etc/fstab.  When doing it using gksudo /etc/fstab, I end up with a blank page referring to a file called fstab' (note the extra character ' character on the end of fstab).  As shown above, you can remedy this problem by enclosing the remaining command in single quotes ie  gksudo 'gedit /etc/fstab' and everything will work fine. :)

---

### Post by TeeAhr1 on 2006-02-25
Thanks, that worked. -pete

---

