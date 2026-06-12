---
title: "[SOLVED] Problems installing from source"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by eilu on 2006-11-05
I just downloaded a couple of applets but can't figure out how to install them. I already have C-compiler (sudo apt-get install build-essential).

First applet: Netspeed 0.13; *./configure* has no problems, but when I type *make* it returns "No targets specified and no makefile found. Stop"

Second applet: xfapplet plugin (to run Gnome panel applets in Xfce); *./configure* returns:
```
*** The required package ORBit-2.0 was not found on your system.
*** Please install ORBit-2.0 (atleast version 2.12.5) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.
```
But I already installed ORBit2 from synaptic (2.14, I think)


What am I doing wrong? :confused:

---

### Post by taurus on 2006-11-05
You also need to install the developing packages if you plan to build something from source.  And normally, there is either README or INSTALL so what does the INSTALL say about how to build the Netspeed 0.13?

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by shortsellyhoonow on 2006-11-05
How do you install a C compiler on ubuntu?

Why on earth doesn't this terrible distro come with a compiler in the first place????

---

### Post by taurus on 2006-11-05
> **shortsellyhoonow said:**
> How do you install a C compiler on ubuntu?

Why on earth doesn't this terrible distro come with a compiler in the first place????
It's on the CD but it doesn't get installed by default!!!

---

### Post by CatKiller on 2006-11-05
> **shortsellyhoonow said:**
> How do you install a C compiler on ubuntu?

The answers in the first post in this thread.

> Why on earth doesn't this terrible distro come with a compiler in the first place????

It does come with a compiler. Perhaps you ought to go and have a cup of tea and calm down before you make any more offensive posts.

---

### Post by po0f on 2006-11-05
eilu,

As taurus stated above, you will need to install the corresponding *-dev packages to actually build programs that use libraries installed on your system.  Most binary distributions (including our beloved Ubuntu) do not install header files with library packages, thus you need to manually install them yourself.

[This](http://packages.ubuntu.com/edgy/libdevel/liborbit2-dev) is the package I believe you are looking for.

---

### Post by eilu on 2006-11-07
> **taurus said:**
> You also need to install the developing packages if you plan to build something from source.  And normally, there is either README or INSTALL so what does the INSTALL say about how to build the Netspeed 0.13?

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

It says:
> The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

---

### Post by bsussman on 2006-11-07
> **shortsellyhoonow said:**
> 
Why on earth doesn't this terrible distro come with a compiler in the first place????

Because the vast majority of ubuntu users will NEVER NEED ONE.

---

### Post by taurus on 2006-11-07
And I suppose you download it somewhere.  On their page, there would be a list of requirements to build it from source.  Look through that list and make sure you have everything on your machine first before you try to build it.

p.s.  When I typed "orbit" in Synaptic, it found a long list but I think you also need liborbit2-dev besides liborbit2!

---

### Post by taurus on 2006-11-07
> **bsussman said:**
> Because the vast majority of ubuntu users will NEVER NEED ONE.
Don't worry about him because he was here to cause trouble so he was banned from this site...

---

### Post by bsussman on 2006-11-09
> **taurus said:**
> Don't worry about him because he was here to cause trouble so he was banned from this site...

hmm - been a long time since I got trolled  :D

---

### Post by eilu on 2006-11-10
oh geez... trolls. *shrug* oh well. I haven't tried anything yet, because uni just started and things are a little busy (they make us use windoze and internet exploder)... I'll try grabbing the liborbit2-dev thingy on the weekend.

---

### Post by eilu on 2006-11-13
](*,) do I feel stupid... netspeed is available on synaptic... d'oh... no need to install from source after all. grrr... lost my brain for a moment there... :redface: 

thanks for the help everyone... *hides under rock*

---

