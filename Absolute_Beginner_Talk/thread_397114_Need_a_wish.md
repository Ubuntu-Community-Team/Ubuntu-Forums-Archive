---
title: "Need a wish"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by PhillD on 2007-03-30
Hi All,

I need to know how I could install wish on XUbuntu.  Don't even know what it is, just know I need it for a script I am trying to run.

Thanks

Phill

---

### Post by adam.tropics on 2007-03-30
wish is in a package called tk8.3 (or .4, or .5) depending I guess what release you are running. I think, it is likely to be tk8.3. So...
```
sudo apt-get install tk8.3
```would do it...

edit. ps. If you want to know a bit more about it, [look here..]("http://www.die.net/doc/linux/man/man1/wish.1.html")

---

### Post by PhillD on 2007-03-30
Thanks for the info and I definitely will look up the info on this.

Just on a side note, how did you know it was in that package?

---

### Post by Skrynesaver on 2007-03-30
Wish is the shell that Tcl/TK scripts run in,

it is part of the tcl  package,

To install 
```

sudo apt-get install tcl

```


This is quite a useful quick and dirty development environment, it allows you wrap shell scripts with a GUi interface

---

### Post by adam.tropics on 2007-03-30
google the terms linux and wish, and you will find the linux man page, linked above. The man page suggests it is to do with Tk, so I fired up synaptic and searched Tk and wish, and presto! There was no magic blue pill I'm afraid, just google!!

---

### Post by adam.tropics on 2007-03-30
from synaptic...(tk8.3)

> 
Tk toolkit for Tcl and X11, v8.3 - run-time files 
Tk is a cross-platform graphical toolkit which provides the Motif
look-and-feel and is implemented using the Tcl scripting language.
This package contains everything you need to run Tk (wish) scripts
and Tk-enabled apps.

Homepage: [http://www.tcl.tk/](http://www.tcl.tk/)

---

