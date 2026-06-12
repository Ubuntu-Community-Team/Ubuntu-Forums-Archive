---
title: "opera not launching"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-09-10
This is what I get whne I try to launch opera...  
[PHP]
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
Segmentation fault
[/PHP]

how to get it to launch?

---

### Post by kellemes on 2007-09-10
[http://my.opera.com/SolimiaN/blog/2007/05/02/error-ld-so-object-libjvm-so-from-ld-preload-cannot-be-preloaded-ignored]("http://my.opera.com/SolimiaN/blog/2007/05/02/error-ld-so-object-libjvm-so-from-ld-preload-cannot-be-preloaded-ignored")

Hope it helps..

---

### Post by beanco on 2007-09-10
i am too much an eternal n00b to quite grasp what has to be done in step 1.

!!!



robi

---

### Post by Terl on 2007-09-10
Try this:

```
sudo apt-get install ubuntu-restricted-extras
```

in the terminal.  It will then ask for a password.  It will download lots of nice goodies, one of which is your java.  Watch the install, as you will have to agree to java terms of agreement.

This will also install the MS TT fonts and mp3 support if you do not have it already.

If you don't need all that, use synaptic to download java.

---

### Post by beanco on 2007-09-10
OK I will get to it in a bit.

I just looked in systems and there is no synaptic!!! that seems strange to me... I do not reall ymind because I never udnerstood how to use it properly... (sg else I have to learn)


I did notice in applications/system tools/jsun java 5.0 console


robi

---

