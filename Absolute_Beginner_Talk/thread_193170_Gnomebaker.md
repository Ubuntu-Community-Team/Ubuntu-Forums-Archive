---
title: "Gnomebaker"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-06-09
Hey all! 

I'm trying to install Gnome Baker on Ubuntu but I'm having a few problems. When I install it through Synaptic it installs fine - but this is a screenshot of what happens when I run the program:
[IMG]http://make-or-break.co.uk/loaded.png[/IMG]

So I tried downloading the .tar.bz2 package but when I run ./configure I get the following:

```

checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

```

Thanks for the help!!!

---

### Post by xXx 0wn3d xXx on 2006-06-09
Hi, I can't understand why it won't open but try to uninstall it and re-install:
> sudo apt-get remove gnomebaker --purge
> sudo apt-get install gnomebaker

If that doesn't work you will need to following to compile from source:
> sudo apt-get install build-essential libxml-parser-perl
Then it will compile.

---

### Post by xXx 0wn3d xXx on 2006-06-09
Hi, I can't understand why it won't open but try to uninstall it and re-install:
> sudo apt-get remove gnomebaker --purge
> sudo apt-get install gnomebaker
If that doesn't work you will need to following to compile from source:
> sudo apt-get install build-essential libxml-parser-perl
Then it will compile.

---

### Post by tartarian on 2006-06-09
I already tried uninstalling and re-installing. 

Thanks for the perl thingy - it worked!!! whoo! Now it says :
```

checking for GNOMEBAKER... configure: error: Package requirements (
        libgnomeui-2.0 >= 2.8.1
        gtk+-2.0 >= 2.4.0
        glib-2.0 >= 2.4.0
        libglade-2.0 >= 2.4.2
        gstreamer-0.8 >= 0.8.9
) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GNOMEBAKER_CFLAGS and GNOMEBAKER_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```
Any ideas?

---

### Post by hellion on 2006-06-11
Oops, NVM.

---

### Post by jobezone on 2006-06-11
Run gnomebaker (version installed through synaptic) in a command line, and post the errors/text you get in the terminal window.

---

### Post by user1397 on 2006-06-11
just look for all of the packages it told you that it hadn't met:
"libgnomeui-2.0 >= 2.8.1,        gtk+-2.0 >= 2.4.0,        glib-2.0 >= 2.4.0, libglade-2.0 >= 2.4.2, gstreamer-0.8 >= 0.8.9"

search for those packages in synaptic and install all of them, and then try it again

---

