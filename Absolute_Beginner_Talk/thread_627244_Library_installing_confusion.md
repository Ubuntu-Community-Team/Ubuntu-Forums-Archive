---
title: "Library installing confusion"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by saltandblues on 2007-11-29
I am trying to install SimDock ([http://sourceforge.net/projects/simdock/](http://sourceforge.net/projects/simdock/)), but the console says I need "libwnck18." I've searched packages.ubuntu.com, and anything similar there I already have. I found it elsewhere, and when I tried to install it, I got this:

```
Unpacking libwnck18 (from libwnck18_2.19.2-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of libwnck18:
 libwnck18 depends on libwnck-common (<< 2.20); however:
  Version of libwnck-common on system is 2.20.1-0ubuntu1.
```

Now, I don't know anything about Ubuntu/Linux and I don't want to mess anything up. It looks like [SimDock will run on Gutsy]("http://ubuntuforums.org/showthread.php?t=622208"), but I don't know where to go from here. Any ideas? Thanks!

---

### Post by p_quarles on 2007-11-29
First, the dependency problem: Simdock should work with a newer version libwnck. The current version (in Gutsy) is libwnck22:
```
sudo apt-get install libwnck22
```
Second, there's a precompiled version of Simdock available here:
[http://www.getdeb.net/app.php?name=SimDock](http://www.getdeb.net/app.php?name=SimDock)

It says it's designed for Feisty, but in all likelihood it will work just fine with Gutsy.

---

### Post by Bart Ellebaut on 2007-12-17
I have installed libwnck22, but still, it won't work. it still needs libwnck18.
so I have copied libwnck22 to libwnck18, but it still stays libwnck18 isn't installed.
what should i do

---

### Post by SOULRiDER on 2007-12-17
There are problems witht he version of the libs. Where are you getting your deb from ?

---

### Post by Bart Ellebaut on 2007-12-17
I have downloaded the .deb from this forum @ Mac4Lin, and I have downloaded another one from the daily ubuntu, and from getdeb.net

I have reinstalled the needed libs.

but still, it won't work

---

### Post by Bart Ellebaut on 2007-12-20
OK, I have solved the problem. I have installed the libwnck 18 from fieste again., and it just works perfectly now.
If anyone is interested, here's the deb. [http://webs.hogent.be/bartellebaut/software/libwnck18_2.15.90-0ubuntu1_i386.deb]("http://webs.hogent.be/bartellebaut/software/libwnck18_2.15.90-0ubuntu1_i386.deb")

Now all you have to do is make a new directory: usr/share/backgrounds, and make an transparant picture, named: warty-final-ubuntu.png, and put it there. then it will work.

have fun

---

