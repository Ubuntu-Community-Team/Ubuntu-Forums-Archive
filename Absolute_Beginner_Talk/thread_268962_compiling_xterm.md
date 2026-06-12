---
title: "compiling xterm"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by k94382 on 2006-10-01
I have installed fluxbox from source on my server install and now I'm pretty sure I need to install a terminal. How do I install the source from

[http://dickey.his.com/xterm/xterm.html](http://dickey.his.com/xterm/xterm.html)

Thanks.

---

### Post by pay on 2006-10-01
The simpile way to compile source code is```
./configure #and options
make
make install
```but do ```
sudo aptitude update
sudo aptitude install build-essential
```first

---

### Post by po0f on 2006-10-01
k94382,

If your server has Xorg installed, it should already have Xterm.  Right-click on the desktop and look for a menu titled Terminals, or something close.  It should be there.  If not, there should be a Run command.  Open that up and type `xterm` into that.

If you are looking for an Xterm replacement, I personally use [rxvt-unicode](http://software.schmorp.de/pkg/rxvt-unicode.html).  You'll need to install libperl-dev and libxft-dev to compile it from source.

---

### Post by k94382 on 2006-10-01
Well, when I right click on the desktop, xterm shows up on the top and I click on that but nothing happens so I assume I have to install it.

---

