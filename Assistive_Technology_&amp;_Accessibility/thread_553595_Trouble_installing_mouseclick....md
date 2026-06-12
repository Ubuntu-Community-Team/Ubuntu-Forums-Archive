---
title: "Trouble installing mouseclick..."
date: 2007-09-18
forum: Assistive Technology &amp; Accessibility
---

### Post by sethlbrown on 2007-09-18
Hey all,

Noob user looking to install a program called mouseclick from source. Downloaded and unpacked mouseclick program from:

[http://www.ufridman.com/mouseclick.html](http://www.ufridman.com/mouseclick.html)

Used standard install method of:

./configure
make
sudo make install

Am unable to resolve a dependency (I'm on Fiesty). All goes well until:

In file included from main.c:14:
mouse_func.h:26:63: error: X11/Xaw/Label.h: No such file or directory
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/seth/mouseclick/src'
make: *** [install-recursive] Error 1

I was able to resolve other dependencies by installing xfce4 and some other packages, but this one eludes me...

For those with RSI, having a program do the clicking is a huge piece of the puzzle. Would appreciate any help I can receive on how to get this mouseclick package up and running or suggestions of alternate programs that serve the same purpose.

---

### Post by sethlbrown on 2007-09-18
Hello everyone, it turns out that error above was not fatal to the application. I'm able to run it out of the src file included with the download despite the dependency error. It seems to work fine.

---

### Post by frafu on 2007-09-21
@sethlbrown

You might have a look at mousetweaks that offers (among others) dwell clicking to the user: 
[http://gerdk.blogspot.com/](http://gerdk.blogspot.com/)

It is being developed for Ubuntu, but is not in its repositories yet. You can find the source code or a debian package for Ubuntu on the site indicated above.

Cheers 

Francesco

---

