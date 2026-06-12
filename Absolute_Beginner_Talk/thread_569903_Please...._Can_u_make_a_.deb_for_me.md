---
title: "Please.... Can u make a .deb for me?"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-10-07
I really need to use a very specific version of BMPx Player. The 0.40.10 (the latest one) But I can't compile it from the source. I tried to follow many guides unsuccessfully. So, after a week, I really want to make a public request.

Please, can anyone make a deb of the 0.40.10 for me and any other person with a limited skills on this particular area?


Thank you so much guys.


ps: In getdeb the latest version available is the 0.40.1

---

### Post by Kosimo on 2007-10-07
By the way, this is the link to get BMPx

[http://bmpx.beep-media-player.org/site/BMPx_Homepage](http://bmpx.beep-media-player.org/site/BMPx_Homepage)

---

### Post by Paulmd on 2007-10-07
> **Kosimo said:**
> I really need to use a very specific version of BMPx Player. The 0.40.10 (the latest one) But I can't compile it from the source. I tried to follow many guides unsuccessfully. So, after a week, I really want to make a public request.

Please, can anyone make a deb of the 0.40.10 for me and any other person with a limited skills on this particular area?


Thank you so much guys.


ps: In getdeb the latest version available is the 0.40.1

What's so special about BMPx, that you can't use one of the many other music players such as XMMS, Rhythmbox, and so on?


XMMS is a really solid media player, and very lightweight. Uses less than 1% of my processor power, playing Ogg Vorbis audio on a celery 566.

there aleady are binary packages for ubuntu.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=bmpx&searchon=names&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=bmpx&searchon=names&version=all&release=all)


in order to complie, you;

1) need gcc installed
2) need the package build-essential installed
3) need to look at the readme to see what OTHER packages you may need to get, or compile. You will also need the -dev version of these packages.

> IN YOUR CASE, YOU NEED INSTALL ALL THESE-- and the -dev version of ALL these packages. Many may already be isntalled.

  * gstreamer               >= 0.10.11
  * gstreamer-plugins-base  >= 0.10.11
  * taglib                  >= 1.4
  * gtk+-2.0                >= 2.10.0
  * gtkmm-2.4               >= 2.10.0
  * cairo                   >= 1.0.0 
  * cairomm                 >= 0.6.0
  * libglade                >= 2.5.1
  * libglademm-2.4          >= 2.6.2
  * libsexymm               >= 0.1.9
  * librsvg                 >= 2.14.0
  * libsoup                 >= 2.2.100
  * libofa                  >= 0.9.3
  * sqlite                  >= 3.3.11
  * libxml                  >= 2.6.1
  * gettext                 >= 
  * dbus                    >= 0.62     (with dbus-glib)
  * Boost                   >= 1.33.1   (with filesystem, regex and iostreams)
  * alsa-lib / libasound    >= 1.0.9    (for linux only)
  * cdparanoia                          (all platforms but solaris)
  * libcdio                 >= 0.70     (for solaris only for the moment)

  Optional:

  * hal                     >= 0.5.7.1
  * startup-notification    >= 0.8
  * libsidplay 1.x (not 2.x)
  * modplug                 >= 0.7
  * NetworkManager          >= 0.6

  Documentation:

  * xsltproc (in libxslt)
  * docbook-xsl-stylesheets


in general, the 3 steps to compiling are, after geting to the terminal

```
./configure
make
make install

```

Notes: not all packages have a ./configure script, in which case, skip to make. If you get "permission denied", use sudo, in front of the commands.

---

