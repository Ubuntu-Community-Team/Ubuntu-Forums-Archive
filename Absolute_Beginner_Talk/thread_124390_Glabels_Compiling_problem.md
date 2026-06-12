---
title: "Glabels Compiling problem"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Screaming Monkey on 2006-02-01
Hello.  I am a noob to linux and the like and am having troubles compiling the newest stable version of Glabels.  I am trying to compile it because of a flaw that I've reported in the version available in Breezy (2.0.2) [[http://sourceforge.net/tracker/index.php?func=detail&aid=1392148&group_id=46122&atid=445116]("http://sourceforge.net/tracker/index.php?func=detail&aid=1392148&group_id=46122&atid=445116")] 

Since they claim to have fixed it in 2.0.4 I got the file, but am having a troublesome time compiling it, I find the directions they give to be severly lacking.  Any help would be welcomed.

---

### Post by davmac on 2006-02-01
Hi,

First thing will be to make sure you've got all of the relevant compilers and libraries installed. If you open up a terminal window and type "sudo apt-get install build-essential" this should sort this out.

The next stages can vary depending on how the package has been put together. Assuming you've downloaded a .tar.gz file the usual way of doing this, in a terminal is

tar -xvzf thepackagename.tar.gz
cd thedirectorynamethathasjustbeencreated
./configure
make
sudo make install

There's some more info about compiling from source at [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

Hope this helps,

Dave Mac

---

### Post by Screaming Monkey on 2006-02-01
Thanks...here goes nothing.

---

### Post by Screaming Monkey on 2006-02-01
I just attempted the compiling procedure and ran into a few problems..
1) after typing ./configure I get this
> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.33 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

 I then typed make and got this 
> *** No targets specified and no makefile found.  Stop.

not sure what all I'm missing exactly as there are a number of working files that are apparently missing.  And then to have no targets specified and no makefile found is really confusing.

How should I proceed from here?

---

### Post by Screaming Monkey on 2006-02-01
After my last post, I searched out some of the missing files and tried again (was able to find all the necessary ones) then typed ./configure and it got to a certain point before I came again upon the > 
*** No targets specified and no makefile found. Stop. 

I looked at what happened at the end of the last configure and saw this message:
> checking for GLABELS... configure: error: Package requirements (glib-2.0 >= 2.2.0 gtk+-2.0 >= 2.0.5 libgnome-2.0 >= 2.0.1 libgnomeui-2.0 >= 2.0.1 libbonobo-2.0 >= 2.0.0 libbonoboui-2.0 >= 2.0.0 libxml-2.0 >= 2.4.23 libgnomeprint-2.2 >= 2.2.0 libgnomeprintui-2.2 >= 2.2.0 libgnomecanvas-2.0 >= 2.0.1 libglade-2.0 >= 2.0.1 ) were not met:

Package libgnome-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnome-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnome-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLABELS_CFLAGS
and GLABELS_LIBS to avoid the need to call pkg-config.

Don't know what to make of this...I think I'll try to find some of these packages, but again, any help would be useful.

---

### Post by kaamos on 2006-02-01
That means you should install the package libgnome2-dev. So if you get errors like this again, copy and paste part the missing package name (like libgnome this time) to the search in synaptic. Look for packages that end with -dev, because the developement libraries are needed for compiling.

"make" won't work if configure has not finished without errors.

A good way to get most of the dependencies:
```
sudo apt-get build-dep glabels glabels-data
```

---

### Post by Screaming Monkey on 2006-02-01
Thank you Thank you Thank you.

I love this community!

by the by, it worked.

now to see if that helped me with the other glabels problems I've been having!:D

---

