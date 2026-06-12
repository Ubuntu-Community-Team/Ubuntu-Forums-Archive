---
title: "Installation paths"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by schizoman on 2007-01-15
As glad as I am to be (mostly) free of Monopolysoft, I'm frustrated by the learning curve.  Mainly, it seems to take me 1/2-1 hour just to find where something is installed by Synaptic Package Manager.  I'm reading a book that's helping me understand the directory structure of Linux, but it's still confusing.  Why, for example, is the default local website under var/www?  What variables?

I've been using Smarty with PHP for some time, now, so I used Synaptic to install Smarty.  Just now, it took me 20 minutes to find out where it's installed.  (And that was only after messing around with 'find' and finally reconfiguring Beagle.)  At least it's in a relatively logical spot.

What's the easiest way to find out the path of an installation?

---

### Post by jordanmthomas on 2007-01-15
a couple of ways:
1.  right click on the package in synaptic and go to properties.  There is an "installed files" tab.  That should help some.
2.  find / -iname 'yourquery'
3.  most config files are in /etc or /usr/share/appname
4.  to find an executable in your PATH:
```
which appname
```

---

