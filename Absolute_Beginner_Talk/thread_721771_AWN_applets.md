---
title: "AWN applets"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by noorez on 2008-03-11
Hi, I've just installed AWN from the repos and I'm trying to install the applets. I downloaded the .tar.gz package but i'm having some trouble building it. After doing a ./configure, here's the error that I get:

configure: error:
  Could not link test program to Python. Maybe the main Python library has been
  installed in some non-standard library path. If so, pass it to configure,
  via the LDFLAGS environment variable.
  Example: ./configure LDFLAGS="-L/usr/non-standard-path/python/lib"
  ============================================================================
   ERROR!
   You probably have to install the development version of the Python package
   for your distribution.  The exact name of this package varies among them.
  ============================================================================

I'm having a bit of trouble figuring what what python packages I need to get so that I can build properly. 

Can someone help out with this ?

---

### Post by FreewareFan on 2008-03-11
I believe what you'll need to do is to install the dev tools that Python uses.  Fire up your Synaptic program, and search for python2.4-dev  and then install that file.  That should do the trick for you.  

Of course, I'm assuming that you already have Python installed on your system??  If not, then also do an install of "Python" too...

Hope this helps!

FwF

---

### Post by ryanhaigh on 2008-03-11
Check out this thread, it will save you the trouble of compiling yourself, I'm using it at the moment and its working great.
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

### Post by noorez on 2008-03-11
I'll take a look at that thanks.

But for the sake of learning how to compile from source, I want to try and sort out the errors:

I went to the Awn Extras page, and ran this command under compiling from source:

pkg-config --modversion awn

and received this error:

Package awn was not found in the pkg-config search path.
Perhaps you should add the directory containing `awn.pc'
to the PKG_CONFIG_PATH environment variable
No package 'awn' found

exactly as the page said it might happen. However, I have the avant-window-manager installed as I am using it....where should I point PKG_CONFIG_PATH to then ? I did install awn using the ubuntu repos...so shouldn't it be in the standard location?

---

### Post by glennric on 2008-03-11
You will need to install the package libawn-dev.

---

### Post by noorez on 2008-03-11
Sweet, I got the ./configure to work.....i'm getting closer.....i hope...

however...make failed....this is the error output:

In file included from affinity.h:32,
                 from applet.c:36:
aff-settings.h:97: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make[4]: *** [applet.lo] Error 1
make[4]: Leaving directory `/home/noorez/Desktop/awn-extras-applets-0.2.6/src/affinity'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/noorez/Desktop/awn-extras-applets-0.2.6/src/affinity'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/noorez/Desktop/awn-extras-applets-0.2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/noorez/Desktop/awn-extras-applets-0.2.6'
make: *** [all] Error 2

---

### Post by glennric on 2008-03-11
There is a good chance that that version of awn-extras-applets is not compatible with the version of avant-window-navigator that is in the repositories.

---

### Post by noorez on 2008-03-11
*sigh*.....hmm.....maybe i'll just go with the version suggested earlier.....i'll leave compiling my own for some other time then :(

Thanks for the help though!

---

### Post by glennric on 2008-03-11
If you really want to compile, download and compile the latest avant-window-navigator source first.  Then try the awn-extras-applets again.

---

### Post by ryanhaigh on 2008-03-12
You can use the command [code]apt-get build-dep avant-window-navigator to download all the dependencies you will need to build the software. Also you may want to look at checkinstall which will create a deb package and install that. 
http://ubuntuforums.org/showthread.php?t=2356

---

