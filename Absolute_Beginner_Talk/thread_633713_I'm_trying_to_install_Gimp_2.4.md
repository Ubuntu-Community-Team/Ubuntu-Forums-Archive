---
title: "I'm trying to install Gimp 2.4"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by watkinsted on 2007-12-06
I have Gimp 2.2 on my system and would like to upgrade to 2.4 and not quite sure how to resolve some of the dependenceis is there and easy way to do this?

---

### Post by dasunst3r on 2007-12-06
Can someone verify that these package will do the trick: [http://www.getdeb.net/app.php?name=Gimp](http://www.getdeb.net/app.php?name=Gimp)

---

### Post by rsambuca on 2007-12-06
> **dasunst3r said:**
> Can someone verify that these package will do the trick: [http://www.getdeb.net/app.php?name=Gimp](http://www.getdeb.net/app.php?name=Gimp)

What Version of Ubuntu are you guys running?  That deb won't work for Dapper, if watkinsted's profile is correct.

---

### Post by watkinsted on 2007-12-06
My profile is correct, I'm running Dapper Drake 6.06 LTS  when I try to configure it tells me I need a newer version of glib, which i downloaded and installed, pango and gtk+ 2.12 which I also did, but it seems the more libraries I try to install the more dependencies I need.

---

### Post by watkinsted on 2007-12-06
When I obtained a few libraries like GLib here are the instructions I was given;


  % gzip -cd glib-2.12.3.tar.gz | tar xvf -  # unpack the sources
  % cd glib-2.12.3                           # change to the toplevel directory
  % ./configure                             # run the `configure' script
  % make                                    # build GLIB

  [ Become root if necessary ]
  % rm -rf /install-prefix/include/glib.h /install-prefix/include/gmodule.h
  % make install                            # install GLIB
and it still doesn't seem to recognize it's there

---

### Post by watkinsted on 2007-12-06
Okay, to be more specific, gtk+-2.12.0 asked me to install glib-2.13.5 which i did. and when I tried to compile gtk again it returns this:

*** 'pkg-config --modversion glib-2.0' returned 2.13.5, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.13.5 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/pub/gtk/](ftp://ftp.gtk.org/pub/gtk/).
is there anything I can do to fix this?

---

### Post by rsambuca on 2007-12-07
I haven't heard of anyone installing the latest gimp onto Dapper yet.  Although it is probably possible, it is going to be very difficult and will likely cause problems with your Dapper installation.  Is it not possible for you to just switch to Gutsy?

---

### Post by watkinsted on 2007-12-07
> **rsambuca said:**
> I haven't heard of anyone installing the latest gimp onto Dapper yet.  Although it is probably possible, it is going to be very difficult and will likely cause problems with your Dapper installation.  Is it not possible for you to just switch to Gutsy?
It probably is, just don't know how difficult that will be on dial up unless I can get it in the mail.  If I remember right, I have to step up to Edgy then Feisty then Gutsy.  That would take me ages on dial up.

---

### Post by Auria on 2007-12-07
Or you can just back up your files and do a clean install from a gutsy CD. Also this way you avoid upgrade problems by using a fresh system.

But to answer your initial question, you would probably need to set
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig

with no warranty it won't break your system :) installing stuff like that against the package management system is always risky

---

### Post by rsambuca on 2007-12-07
> **watkinsted said:**
> It probably is, just don't know how difficult that will be on dial up unless I can get it in the mail.  If I remember right, I have to step up to Edgy then Feisty then Gutsy.  That would take me ages on dial up.

Why don't you just order the Gutsy CD's from shipit?  You can then install a fresh system and have the newer packages.

---

