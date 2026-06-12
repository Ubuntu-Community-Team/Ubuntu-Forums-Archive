---
title: "Trouble installing GTK2...plz help"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Nectron on 2006-09-20
I'm trying to install GTK2 and it's required dependencies..
It basically requires:
GLib 2.12
Pango 1.13
ATK 1.9 
and cairo 1.2.

I've downloaded the required dependencies and first installed Glib 2.11.4..

When I tried installing ATK-1.12.2, I got the following error..
```

checking for GLIB - version >= 2.5.7...
*** 'pkg-config --modversion glib-2.0' returned 2.11.4, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

```

I'm truly lost here.. I tried fetching everywhere to find a solution but I couldn't.

Your suggestions are of great importance to me, anything is welcome!

Thanks in advance ;)

---

### Post by skymt on 2006-09-20
You really aren't supposed to insall GTK from source. You should already have it. If you don't, apt it: "sudo aptitude install libgtk2.0". If you need the development files for it: "sudo aptitude install libgtk2.0-dev".

---

### Post by Nectron on 2006-09-20
Thanks for the quick reply, but I tried the commands you listed and neither one of them works..

Nothing is found to match them..

---

### Post by skymt on 2006-09-20
Sorry, I got the first one wrong. It's "sudo aptitude install libgtk2.0-0". The -dev one should have worked though.

Try running "cat /etc/apt/sources.list" and posting the output.

---

### Post by blkdragon on 2006-09-26
hey if you follow the instructions at [http://lihavim.wordpress.com/2006/08/06/install-gtk-2100/](http://lihavim.wordpress.com/2006/08/06/install-gtk-2100/)

then it works.

at least, it worked for me.

---

