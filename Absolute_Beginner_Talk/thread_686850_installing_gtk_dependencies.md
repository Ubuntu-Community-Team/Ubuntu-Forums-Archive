---
title: "installing gtk dependencies"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by indianrivalry on 2008-02-03
I'm trying to install gtk because I need it for a theme I want. I get this error when trying to install atk:

*** 'pkg-config --modversion glib-2.0' returned 2.12.9, but GLIB (2.14.1)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

how do i fix this?

Thanks

---

### Post by viciouslime on 2008-02-03
GTK is absolutley integral to an Ubuntu system. it is the toolkit used by gnome and all gnome applications to draw every button, form, tick-box, scroll bar, etc. that you see on the screen. In other words, you already have it...

Which theme are you trying to get working? it is probably something else that you need to install. If you send me a link to the theme, I'll try and help you out :)

---

### Post by indianrivalry on 2008-02-03
i thought i needed to install a newer version of gtk because the theme is for gtk 2.x.x

[http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438](http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438)

---

### Post by viciouslime on 2008-02-03
You already have 2.12 as comes with ubuntu. That isn't actually a theme, but an engine AND a few themes.

You will need to install the package build-essential using the command:

sudo apt-get install build-essential

Then follow the instructions given by the theme:

To install the theme engine extract it to somewhere convenient and in that directory,
run: "./configure --prefix=/usr" then "make"
For animation support add "-enable-animation" when running "./configure"
Then as a root user "make install".


:)

---

### Post by viciouslime on 2008-02-03
EDIT: Found an EVEN better link to latest version as a deb:

[http://www.gnome-look.org/content/show.php/Aurora+Ubuntu+Package?content=62227]("http://www.gnome-look.org/content/show.php/Aurora+Ubuntu+Package?content=62227")

---

### Post by indianrivalry on 2008-02-03
im getting a problem actually... it's telling me i dont have gtk

checking for GTK... no
configure: error: GTK+-2.10 is required to compile aurora

---

### Post by viciouslime on 2008-02-07
> **indianrivalry said:**
> im getting a problem actually... it's telling me i dont have gtk

checking for GTK... no
configure: error: GTK+-2.10 is required to compile aurora

Ah, that doesn't mean that you don't have gtk. That means that you don't have the development libraries for gtk.

You need to install the packages ending in -dev

If you use the link to the deb file i gave you though, you don't need to compile anything. I've tested it and it does work.

---

