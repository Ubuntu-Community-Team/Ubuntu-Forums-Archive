---
title: "Cygwin help"
date: 2012-04-23
forum: Any Other OS
---

### Post by blithen on 2012-04-23
So I'm trying to install CMus on cygwin and Cmus actually boasts about being able to be installed under cygwin but I've installed every development package I can think of and then some and it's still not getting passed the make stage here is where it errors:
```

Sparky@Sparky-PC ~/cmus-v2.4.3
$ make
   CC     waveout.lo
waveout.c:1:0: warning: -fPIC ignored for target (all code is position independent)
waveout.c: In function 'waveout_get_option':
waveout.c:284:3: error: implicit declaration of function 'snprintf'
waveout.c:284:3: warning: incompatible implicit declaration of built-in function 'snprintf'
scripts/lib.mk:76: recipe for target `waveout.lo' failed
make: *** [waveout.lo] Error 1

```
Any linux gurus care to shed some light?

---

### Post by davetv on 2012-04-23
I got 2 thoughts

(1) first run ./configure
(2) find out if the gcc in your cygwin is a compatible version

---

### Post by blithen on 2012-04-23
Yeah I ran ./configure, and what's gcc? D:

---

### Post by blithen on 2012-04-26
I think the current stare of cygwin and Cmus don't allow the two to be compatible I installed every package Cygwin repos had, and a few others that I thought might help the make work, but no dice. Oh well. ^^ Winamp does me well anyway.

---

