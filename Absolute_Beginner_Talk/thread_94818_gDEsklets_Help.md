---
title: "gDEsklets Help"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by nierz on 2005-11-24
I am trying to use gDesklets, but I can't understand the installation steps, in the readme this is all it says:

>   First make sure that you have all necessary dependencies installed on your system!
  In addition to that you also need the (gtk/gnome) python devel packages.
  If you're new to Linux please don't try to compile gDesklets; it's for your
  own protection.

   $ ./autogen.sh (if you're compiling a CVS version)
   $ ./configure
   $ make
   $ su -c "make install"

  If you want 'gDesklets' to appear on the GNOME menu, be sure to
  put it where GNOME can find it, e.g.:
  $ ./configure --prefix=/usr --sysconfdir=/etc

I installed all the dependencies, I just have no idea what the above instructions mean or what I'm suppost to do with them.

---

### Post by oskude on 2005-11-24
whats wrong with installing gdesklets through synaptics ?
or whats wrong with "sudo apt-get install gdesklets" ?

edit:
ok, you need "universe" for that: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

i wonder why "universe" and "multiverse" are not default on ubuntu install ?
its like "ALL" need them ;)

---

### Post by xelink on 2005-11-25
thanks dude.... I was trying to figure this out myself just now...

---

