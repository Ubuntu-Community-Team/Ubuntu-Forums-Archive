---
title: "kismet help with libs"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by frostbytes on 2007-08-11
```
checking for group 'root'... yes
checking for group 'man'... checking for initscr in -lncurses... no
configure: WARNING: Unable to find libncurses
checking for initscr in -lcurses... no
configure: error: Unable to find libncurses or libcurses

```

I'd getting this lib error at ./configure when trying to install kismet.  I have checked synaptic and the libs are installed, but they are not showing in /usr/lib.  if anyone can help me figure out why this is, Id appricate it.  Thanks!

---

### Post by Hans5849 on 2007-08-13
I was having the same problem, a google search turned this up which works for me. 
sudo apt-get install libncurses5-dev

---

