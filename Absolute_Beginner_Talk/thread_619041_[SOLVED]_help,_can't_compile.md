---
title: "[SOLVED] help, can't compile"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-11-21
um everytime (3 times on dif. packages now) i haven't been able to compile. the error message sems always to be the asme:
```
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables

```

So how do I get this stuff to compile? then I can move on to make install...

sv

thanks in advance :)

---

### Post by jordanmthomas on 2007-11-21
Ubuntu does not come with any way of compiling c code (a bit weird, if you ask me)

You need to install gcc
```
sudo apt-get install build-essential
```
will get you everything you need to build simple stuff.  If your configure complains about things being missing, look for packages named like this:
```
whateverismissing-dev
``` and install it.

---

### Post by Perfect Storm on 2007-11-21
Have you checked if that application you want to compile is in synaptic package manager first?

---

### Post by staticvoid on 2007-11-21
Thank you both!  :)

It's not in synaptic. At least, I don't think so. GD image manipulation? perhaps?

sv

---

### Post by staticvoid on 2007-11-21
> **jordanmthomas said:**
> Ubuntu does not come with any way of compiling c code (a bit weird, if you ask me)
it asked for the cdrom when I told it to apt-get.

```
After unpacking 31.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

```

sv:guitar:

---

### Post by 3rr0r on 2007-11-21
> **staticvoid said:**
> it asked for the cdrom when I told it to apt-get.

```
After unpacking 31.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

```

sv:guitar:

so put it in?

---

### Post by staticvoid on 2007-11-21
haha, right, I was just pointing out that ubuntu does come with a C compiler, but just does not move it from the cd to the computer. at least.... thats what it looks like!  haha, i'm not *that* much of a n00b  :P hehehe

sv

---

### Post by staticvoid on 2007-11-21
and i shoulda marked this as solved, my bad

---

