---
title: "Lost in a sea of dependencies"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by flyer23 on 2007-04-16
:confused: I need GTK that needs ATK that needs Glib that needs Pango that needs Xrender of which the headers aren't found.  Not necessarily in that order, but you get the idea.  I'm going around and around in a loop of dependencies.  

I have build-essentials and some of the library files that were clearly missing, but at this point I'm stuck and can't seem to compile anything because of something else missing. Any ideas what my next move should be?

---

### Post by NeoLithium on 2007-04-16
Well, different programs do have different dependencies, what were you trying to compile when all the errors came up?

---

### Post by Maestro23 on 2007-04-16
Welcome to the world of compiling from source.  Always check the repositiories first.  If they don't have the program, then go to the program's site and look for a .deb, .rpm, .bin.  There is no easy way when compiling strictly from source.

You have probably seen these links, but I will post them again anyway.

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Good luck man.

---

### Post by flyer23 on 2007-04-16
It really has been a round robin of the files I cited.  The last effort in the string of nastiness was an attempt to compile xrender, but the headers are not found.  Here is what I was getting

```
checking X11/extensions/render.h presence... no
checking for X11/extensions/render.h... no
configure: error: Render headers not found.
tim@tim-desktop:~/Downloads/xrender-0.8.3$
```

---

### Post by ComplexNumber on 2007-04-16
> **flyer23 said:**
> :confused: I need GTK that needs ATK that needs Glib that needs Pango that needs Xrender of which the headers aren't found.  Not necessarily in that order, but you get the idea.  I'm going around and around in a loop of dependencies.  

I have build-essentials and some of the library files that were clearly missing, but at this point I'm stuck and can't seem to compile anything because of something else missing. Any ideas what my next move should be?
when you're compiling programs from source and the configure script is complaining that several dependencies aren't met, it is important to remember that you must install the "dev" version of the packages that its complaining about. for example, if it complains that glib-2.0 isn't installed, install glib-2.0**-dev**. 

here is an explanation as to why you need to install the dev version:
when you compile a program from source, the configure script look in the following 2 directories to see if it can find those dependencies:
/usr/lib/pkgconfig
/usr/local/lib/pkgconfig
in each of those directories you will see lots of "pc" files for lots of different packages. for example, there will be a file called gtk.pc, a file called, glib.pc, a file called mozilla-firefox.pc,  etc etc. when the configure script checks to see if the dependencies are met and it  sees glib.pc, it will look at the version number stated to decide if the version number is up to date enough to satisfy the dependency.
now, its important to remember that when you install (for example) glib-2.0-dev, it also installs the associated "pc" file that goes in one of the above 2 directories. but when you install glib-2.0, it doesn't.

hope that made sense.

---

### Post by flyer23 on 2007-04-16
Yes it made sense.  Thanks for the info.  I'm go to go spend some more time hunting the dev  files and see if I can't get one of the packages rolling again.

---

