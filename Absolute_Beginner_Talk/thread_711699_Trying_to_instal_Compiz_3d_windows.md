---
title: "Trying to instal Compiz 3d windows"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by alarson82 on 2008-02-29
I am trying to follow the steps at this location
[http://ubuntuforums.org/showthread.php?t=659282](http://ubuntuforums.org/showthread.php?t=659282)

when I get to the code: Make I type in in the terminal and get this

andrew@ubuntu:~/compiz/3d$ make
bcop'ing : build/3d.xml -> build/3d_options.h/bin/sh: --header=build/3d_options.h: not found
make: *** [build/3d_options.h] Error 127

and when i run 'sudo make install' i get the same area.

Any ideas?
__________________

---

### Post by genus_001 on 2008-03-01
I had the same problem.
Did you install the packages required for compiling plugins?  They arent installed by default.  So you might have skipped the first part of the howto because you have CCSM already installed, but make sure you follow all of the steps that follow, starting with number one.  
When it wouldn't work for me i had to run:

sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool

I hope that I have been helpful, good luck!

---

