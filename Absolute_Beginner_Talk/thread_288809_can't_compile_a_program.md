---
title: "can't compile a program"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-10-30
I'm trying to compile this game :
[http://kralovstvi.sourceforge.net/](http://kralovstvi.sourceforge.net/)
and the dependencies are killing me

maxim@maxim:~/maxddark/games/8Kingdoms-1.0.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether byte ordering is bigendian... no
checking for X... libraries , headers 
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.1.6... yes
checking for Mix_OpenAudio in -lSDL_mixer... yes
checking for OpenGL support... yes
checking for XML_ParserCreate in -lexpat... no
configure: error: Expat library required


what exactly do I need more ?

---

### Post by ceargle on 2006-10-30
There are a few Expat packages in Synaptic, I'd try libexpat1 and libexpat1-dev first, then the others if necessary.

Hope this helps.

Bryan

---

### Post by Iarwain ben-adar on 2006-10-30
Hi,
try this:

```
sudo aptitude install expat
```


Iarwain

---

### Post by Iarwain ben-adar on 2006-10-30
sorry,
double post :D


Iarwain

---

### Post by Ben Sprinkle on 2006-10-30
> **Iarwain ben-adar said:**
> Hi,
try this:

```
sudo aptitude install expat
```


Iarwain
```
sudo apt-get install expat
```
Is what you mean?

---

### Post by maaronB on 2006-10-30
> **synectics said:**
> ```
sudo apt-get install expat
```
Is what you mean?

Is there a big difference between aptitude and apt-get?

---

### Post by Ben Sprinkle on 2006-10-30
I have posted this before, but aptitude and apt-get are **exactly the same**, there is nothing different. I don't know if you can do aptitude install though.

---

### Post by Perfect Storm on 2006-10-30
aptitude is better to solve dependency. Also if you install something big, like meta-packages as Kubuntu-desktop you can remove all the meta-packages dependency if you want to uninstall kubuntu-desktop.
When compiling sources in most cases you need the -dev and/headers for the packages, therefore;
```
sudo aptitude install libexpat1 libexpat1-dev
```

---

### Post by konst88 on 2006-10-30
1. you can do aptitude install
2. patitude and apt-get are not the same. aptitute doing the same as apt-get, but much better.
there are plenty of threads on the forums about the difference.
3. dont use apt-get, only aptitude.

---

### Post by Ben Sprinkle on 2006-10-30
Ah thanks, AI. Cleaned it up a bit for me, didn't know it solved the depend's.
Thanks.

---

### Post by MaximB on 2006-10-30
ok...I've tried all that you suggested and installed bunch of other stuff, but to no use
here what I get now :

maxim@maxim:~/maxddark/games/8Kingdoms-1.0.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether byte ordering is bigendian... no
checking for X... libraries , headers 
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.1.6... yes
checking for Mix_OpenAudio in -lSDL_mixer... yes
checking for OpenGL support... yes
checking for XML_ParserCreate in -lexpat... yes
checking for Tcl_Main in -ltcl... no
configure: error: TCL library required

---

### Post by ceargle on 2006-10-30
The last two lines read:

```
checking for Tcl_Main in -ltcl... no
configure: error: TCL library required
```

This means you are missing some sort of TCL library.  Search for TCL in Synaptic, and try installing some of the TCL libraries.

```
sudo apt-get install libtcltk-ruby
```

..may work.  If not, trying installing some of the other libraries.  Whenever I get building errors, I just try installing the packages mentioned in the 
```
configure: error:
```
line.  This will solve 75% of your dependency problems when building.

---

### Post by mysticrider92 on 2006-10-30
Have you looked in Synaptic for the game? In Ubuntu, I have found that compiling packages from other sources causes tons of very confusinge dependancy problems (packages with different names, or conflicting with other packages). It is much easier to do everything from the repositories.

---

### Post by MaximB on 2006-10-30
I know but I got the source files from the site...the game is not officially supported.
but should work under Linux

and it's a real hell - it didn't work, the dependencies I mean.
it's a Pain in the Azz to find them.

---

### Post by Ben Sprinkle on 2006-10-31
Every time you try to compile and it's missing files, just install in synaptic.
Try using this if you have make and makeinstall.
```

./configure && make && makeinstall
```

---

### Post by MaximB on 2006-10-31
"checking for Tcl_Main in -ltcl... no
configure: error: TCL library required"
there are tons of TCL libraries, and I don't know what to install
I've tried what you suggested but to no avail.

is there a command to ./configure and install all dependencies automatically ?

---

### Post by bonzodog on 2006-10-31
Welcome to the wonderful world of building software.

You will need to work through each of the dependencies separately. Always install the depend build/dev packages off synaptic as that will resolve depends for the depends that you need. This is sometimes known as Dependency Hell.

But, I find that building programs is an intuitive process and there is much to be learnt.

Learn to read through the ./configure output as it runs. Configure runs checks for certain libraries and programs that the program you are building needs to run.

in this case, you will need the tcl/tk environment, I think you will find.

---

