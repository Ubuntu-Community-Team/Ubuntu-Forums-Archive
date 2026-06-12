---
title: "Installing Scribus"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Shaktipwr on 2007-07-20
I am installing Scribus 1.3.3.9 on my ubuntu feisty.  When trying to configure I am told:

The required library libfreetype could not be found. See the BUILDING file.

You may need to install some additional libraries or packages (on Linux,
that may mean -dev or -devel packages too). Also check your environment
variables. If you're on a 64 bit machine, maybe you need to add
--enable-libsuffix=64 to the configure arguments.
See the BUILDING file for further details and troubleshooting information. 
This library is required for Scribus to build. Configure will now terminate

The "libfreetype" was "libart"  but I found that.  So upon looking at Building there are all sorts of things I need to get to install Scribus and I can't seem to find anything.
I am super new to Linux so be easy with me.  I have spent the last hour looking at different forums and searching the net for my answer but can find nothing.  Here is the list of libraries I need:
        Qt >= 3.3 (3.3.7+ recommended)
	Freetype >= 2.1.3 (2.2.1+ strongly recommended)
	libart >= 2.3.10+ (2.3.17+ recommended)
	libtiff >= 3.6.0
	LittleCMS (liblcms) = 1.12 (1.15+ recommended)
	libjpeg (depending on how Qt is packaged)
	libpng

and

        CUPS
	Fontconfig >= 2.0
	LibXML2 >= 2.6.0
	GhostScript >= 8.0 (8.15 or greater preferred)
	Python >= 2.3
	tkinter for the font sampler script
	python-imaging for the font sampler preview
	pkgconfig (to assist finding other libraries)

If I am being a total dumbbutt please be nice to me.....I am learning my way through this on my own. Thanks!

---

### Post by testube_babies on 2007-07-20
Avoid compiling:
[http://www.getdeb.net/app.php?name=Scribus](http://www.getdeb.net/app.php?name=Scribus)

After you install it you may need to "sudo apt-get install -f" to clear up some dependency issues.

---

### Post by Shaktipwr on 2007-07-20
Well now, wasn't that amazingly easy.  Thanks!

---

