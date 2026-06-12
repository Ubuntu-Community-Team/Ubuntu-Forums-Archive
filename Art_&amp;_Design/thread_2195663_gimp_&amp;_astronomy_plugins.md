---
title: "gimp &amp; astronomy plugins"
date: 2013-12-25
forum: Art &amp; Design
---

### Post by kurja on 2013-12-25
I guess this goes here, since it's about gimp?

I've been trying my hand at astrophotography, and would like to try [gimp-plugin-astronomy]("http://registry.gimp.org/node/2352") but I can't figure out how to get it all working in gimp; there are instructions included, but I fail at "make".

```
LINUX
=====
To install gimp-plugin-astronomy on Linux systems, please install gimp*-dev package, gsl-dev package,
make and gcc (this should also install the necessary packages gtk*-dev, glib*-dev, etc.).
Then do
	tar -xvjf gimp-plugin-astronomy-VERSION.tar.bz2
	cd gimp-plugin-astronomy-VERSION
	./configure
	make
	su
	<password>
	make install

```

Anyone here tried stacking star field images in ubuntu? I have a version of Regis that takes .arw files but there's a steep learning curve for that... at this point I'd really like something more simple and less sciency, I'm really just looking froward to making some pretty pictures, not serious astronomy. Primarily, what I'm looking for is a simple way to align and median-stack the short exposures that I make (without using a tracking mount). I've had some success with align_image_stack from huginn tools, but that's pretty much it :/

Any advice?

---

### Post by timsdeepsky on 2013-12-25
This is a tough one....I am an astrophotographer myself,,and have struggled for a few years to find suitable linux programs for this....What are you using to take your short exposures??..DSLR??..Imager??..Through a telescope??..Or wide field....Also,,how many exposures on average do you stack??..I would like to know these things about your setup if i could please....Thanks...To make it easy on yourself,,you may have to use "Registax" in Wine to actually get what you want....The derotation of the stars in the stack was always the problem i ran into with linux,,not the stacking....Also,,there used to be a Debian package in the software center called "Ale",,and this was an awesome command line stacking package(and i believe field de-rotating when used with imagemajick)....

---

### Post by steeldriver on 2013-12-25
in what way does the 'make' fail (what is the error message exactly)? is it an error about gtk_box_new?

---

### Post by kurja on 2013-12-26
> **timsdeepsky said:**
> This is a tough one....I am an astrophotographer myself,,and have struggled for a few years to find suitable linux programs for this....What are you using to take your short exposures??..DSLR??..Imager??..Through a telescope??..Or wide field....Also,,how many exposures on average do you stack??..I would like to know these things about your setup if i could please....Thanks...To make it easy on yourself,,you may have to use "Registax" in Wine to actually get what you want....The derotation of the stars in the stack was always the problem i ran into with linux,,not the stacking....Also,,there used to be a Debian package in the software center called "Ale",,and this was an awesome command line stacking package(and i believe field de-rotating when used with imagemajick)....

I'm using just a dslr with ordinary camera lenses, no telescope. At this point I don't stack any number of exposures on average, because I'm mostly pulling hair when trying to stack any of them ;) But, by the look of things, I'd be putting together maybe 15 to 25 light frames.

I've been under the impression that Registax would be primarily for stacking lunar/planetary images? Ale I haven't tried, I have to try out those two.

---

### Post by kurja on 2013-12-26
> **steeldriver said:**
> in what way does the 'make' fail (what is the error message exactly)? is it an error about gtk_box_new?

When entering just ```
make
``` like it says in the instructions, I get ```
make: *** No targets specified and no makefile found.  Stop.


```

---

### Post by steeldriver on 2013-12-26
OK well that error basically means that the ./configure step failed - usually that's because your system is missing one or more of the *prerequisites* (aka build-deps)

You will need at least a complete GNU C compiler environment (gcc and libc6-dev) - the easiest way to get those is to install the build-essential package - plus the headers and libraries for the Gtk+ toolkit on which gimp is based (libgtk2.0-dev). You can either install those via your favourite GUI package manager or on the command line using apt-get

```
sudo apt-get install build-essential libgtk2.0-dev
```

After that, run the ./configure step again and make a note of any other things it complains about - if it doesn't complete successfully, you will need to puzzle out and install further build-deps

FWIW I was able to build and install the plugin on my 12.04.3 box (running gimp 2.6.12) although there is an issue with the source code that I mentioned in my previous post - but I don't have any astro images to test it

---

### Post by kurja on 2013-12-26
Uh, embarrassed - I thought I had those installed but apparently not :oops:

after installing those ./configure spits out the following 

 ```
./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking gsl/gsl_version.h usability... no
checking gsl/gsl_version.h presence... no
checking for gsl/gsl_version.h... no
checking for gsl_version in -lgsl... no
checking fftw3.h usability... no
checking fftw3.h presence... no
checking for fftw3.h... no
checking for fftw_execute in -lfftw3... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GIMP... configure: error: Package requirements (gimp-2.0 >= 2.4.0 gimpui-2.0 >= 2.4.0) were not met:


No package 'gimp-2.0' found
No package 'gimpui-2.0' found


Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.


Alternatively, you may set the environment variables GIMP_CFLAGS
and GIMP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

...gimp-2.0 >= 2.4.0??

Do I need to be in a specific folder where I'm making this? I just extracted the astronomy plugin archive under /usr/share/gimp/2.0

---

### Post by kurja on 2013-12-26
I guess I need the libgimp*-dev package at least

---

### Post by steeldriver on 2013-12-26
yes try installing libgimp2.0-dev

```
libgimp2.0-dev - Headers and other files for compiling plugins for GIMP
```

What version of Ubuntu are you running btw?

---

### Post by kurja on 2013-12-26
> **steeldriver said:**
> yes try installing libgimp2.0-dev

```
libgimp2.0-dev - Headers and other files for compiling plugins for GIMP
```

What version of Ubuntu are you running btw?

Yea that's what I meant with libgimp*-dev. I'm using the latest LTS, 12.04.

After installing the libgimp2.0-dev with synaptic ./configure seems to be happy but make ends with this:

```
make[2]: Entering directory `/usr/share/gimp/2.0/gimp-plugin-astronomy-0.8/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -pthread -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/gtk-2.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/gimp-2.0 -I/usr/local/include -DLOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gimp-plugin-astronomy"\"   -g -O2 -Wall -MT alignment.o -MD -MP -MF ".deps/alignment.Tpo" \
	  -c -o alignment.o `test -f 'alignment.c' || echo './'`alignment.c; \
	then mv -f ".deps/alignment.Tpo" ".deps/alignment.Po"; \
	else rm -f ".deps/alignment.Tpo"; exit 1; \
	fi
alignment.c:39:30: fatal error: gsl/gsl_multifit.h: No such file or directory
compilation terminated.
make[2]: *** [alignment.o] Error 1
make[2]: Leaving directory `/usr/share/gimp/2.0/gimp-plugin-astronomy-0.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/share/gimp/2.0/gimp-plugin-astronomy-0.8'
make: *** [all] Error 2



```

---

### Post by steeldriver on 2013-12-26
OK that's part of libgsl0-dev (GNU Scientific Library (GSL) -- development package)

In the way of 'teach a man to fish', there's a really great utility called apt-file that lets you do reverse lookup in situations like this

```

sudo apt-get install apt-file

sudo apt-file update # <-- don't need to do this every time

```

then 
```

$ apt-file search 'gsl/gsl_multifit.h'
libgsl0-dev: /usr/include/gsl/gsl_multifit.h

```

Saves a lot of guesswork!

---

### Post by kurja on 2013-12-26
Thanks for that, there was one more missing package. Now I got it all "make'd" and tools appear in gimp under astronomy... we'll see how the alignment works :^/

---

### Post by kurja on 2013-12-27
Very much underwhelmed by the results, but Deep Sky Stacker for windows surprisingly works in ubuntu with very little work - dss website tells a "scary tale" of recompiling wine and so forth, but all I needed was one .dll file and it just works. Marking this as solved now.

---

### Post by prokodine on 2014-01-08
There's also [http://sourceforge.net/projects/lxnstack/](http://sourceforge.net/projects/lxnstack/), and there are a few commercial options.

---

